---
name: muapi-3d-render
description: Генерация брендовых 3D-стиль визуалов для сайта MM-Express через MuAPI REST API (x-api-key). Использовать, когда Дизайнеру/Backend нужны hero-сцены, 3D-иконки, иллюстрации в палитре бренда MM-Express.
metadata:
  type: reference
---

# MuAPI 3D-render skill (REST, по API-ключу)

MuAPI — унифицированный REST API к 100+ image/video-моделям (Flux, GPT-image, Imagen4,
Seedance, Kling и т.д.). Работает **по API-ключу через заголовок `x-api-key`**, НЕ через MCP.
Ключ лежит в секрете окружения `MUAPI_KEY` — **никогда не печатать его в логах/комментариях**.

> Про «3D»: MuAPI отдаёт **картинки/видео**, в т.ч. фотореалистичный **3D-стиль рендер**
> (изометрия, studio light), но НЕ glTF-меши. Для статичных 3D-визуалов/иконок/иллюстраций —
> идеально. Если нужен **интерактивный вращаемый 3D** в hero — отдельный трек (Spline/Blender
> → glTF), MuAPI закрывает статичные 3D-визуалы и кадры анимации.

## Поток (async: submit → poll → download)

### 1. Отправить задачу
```bash
curl -s -X POST "https://api.muapi.ai/api/v1/flux_dev_lora_image" \
  -H "x-api-key: $MUAPI_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "prompt": "<brand-locked prompt, см. ниже>",
    "width": 1600,
    "height": 1200,
    "num_images": 1
  }'
```
Ответ:
```json
{ "request_id": "abc123xyz", "status": "processing",
  "cost": { "amount_usd": 0.0042, "amount_credits": 1 } }
```
Сохранить `request_id`.

### 2. Опросить результат
```bash
curl -s "https://api.muapi.ai/api/v1/predictions/<request_id>/result" \
  -H "x-api-key: $MUAPI_KEY"
```
Опрашивать раз в 2–4 c, пока `status` не станет `completed`:
```json
{ "id": "abc123xyz", "status": "completed",
  "outputs": ["https://cdn.muapi.ai/...output.png"] }
```
Готовый файл — `outputs[0]`.

### 3. Скачать и оптимизировать
Скачать `outputs[0]`, сохранить в `client/public/3d/`, дать осмысленное имя, ужать вес
(PNG@2x для ретины; для прозрачного фона запрашивать в prompt «transparent background»).

## Бренд-замок для prompt (Brand Book v1.0.1 — соблюдать строго)

Каждый prompt фиксирует палитру и стиль:
```
isometric 3D render, logistics theme, MM-Express brand palette:
deep navy #002858 main bodies, Cargo Amber #E8A33D accents (small, <=10%),
kraft cardboard boxes, soft studio lighting, clean light background (#F7F8FA),
high detail, octane-style render, no text, no logos, centered, product-shot
```
- Hero-сцена коридора: добавить «KG factory -> truck/container -> Moscow warehouse ->
  handoff to marketplace, route arcs, floating UI data chips».
- 3D-иконки сервисов: «single object 3D icon, navy+amber, transparent background,
  consistent set» (доставка/фулфилмент/трекинг/таможня/склад/маркировка).
- Тёмный hero (опция): фон `#0F172A`, amber-glow, остальное то же.
- Запрещено: чужие палитры, сток-вид, текст на картинке, посторонние логотипы.

## Дисциплина расходов / гардрейлы
- Генерить пачками по 1–2 варианта на ассет, выбирать лучший — потом масштабировать.
- Перед массовой генерацией (>10–15 изображений) — оценить cost по полю `cost.amount_usd`
  из ответа и согласовать объём с Основателем (категория «расход»).
- Ключ `MUAPI_KEY` — только из секрета, не хардкодить, не выводить.
- Ассеты идут в `client/public/3d/`, подключаются Web Engineering с lazy-load.

## Когда НЕ использовать
- Для интерактивного вращаемого 3D-объекта (нужен glTF/Spline — отдельный трек).
- Для парсинга/данных (это Apify, через MCP).
