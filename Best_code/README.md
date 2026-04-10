## Лучший результат на public
- 0.91931
## Результаты

- **Лучшая модель:** FPN (seed 42)
- **Лучший Validation Dice:** 0.9164 (эпоха 80)
- **Лучший Validation IoU:** 0.8588 (эпоха 64)
- **Ансамбль (UNet++ + FPN):** сабмишен `submission_ensemble.csv`

## Модели

### UNet++
- **Архитектура:** UnetPlusPlus
- **Энкодер:** timm-efficientnet-b3
- **Предобучение:** ImageNet
- **Лучший результат:** seed 9999, Dice = 0.9120

### FPN
- **Архитектура:** FPN (Feature Pyramid Network)
- **Энкодер:** timm-efficientnet-b3
- **Предобучение:** ImageNet
- **Лучший результат:** seed 42, Dice = 0.9164

## Обучение

Мы обучили две архитектуры (UNet++ и FPN) на трех различных сидах (2026, 9999, 42). Лучшие результаты показала модель **FPN с seed = 42**.

**Параметры обучения:**
- Эпох: до 80 (с ранней остановкой)
- Размер батча: 4
- Размер изображения: 512x512
- Оптимизатор: AdamW (LR=3e-4, Weight Decay=1e-4)
- Функция потерь: Combined Loss (BCE + Dice)
- Планировщик LR: ReduceLROnPlateau
- Аугментация: HorizontalFlip, VerticalFlip, RandomRotate90

## Ансамблирование

Для улучшения качества мы собрали ансамбль из лучших моделей:
- **UNet++** (seed 9999) + **FPN** (seed 42) с равными весами (0.5 / 0.5)
- Использована TTA (Test Time Augmentation)
- Результат сохранен в `submission_ensemble.csv`

## Лучшие метрики по моделям и сидам

| Модель | Seed | Лучший Dice | Эпоха | Лучший IoU | Лучший Loss |
|--------|------|-------------|-------|------------|-------------|
| FPN | 42 | 0.9164 | 80 | 0.8588 | 0.0736 |
| FPN | 9999 | 0.9088 | 30 | 0.8452 | 0.0682 |
| FPN | 2026 | 0.9058 | 33 | 0.8483 | 0.0714 |
| UNet++ | 9999 | 0.9120 | 39 | 0.8505 | 0.0640 |
| UNet++ | 42 | 0.9103 | 24 | 0.8510 | 0.0729 |
| UNet++ | 2026 | 0.9070 | 42 | 0.8503 | 0.0684 |

## Веса моделей

https://drive.google.com/drive/folders/1-1phCtUWiTU8LPMCXBHtyJ6uNNjxaiZF

## Таблицы с метриками по эпохам

- [FPN seed 42 (лучший)](history_seed_0042.csv)
- [FPN seed 9999](history_seed_9999.csv)
- [FPN seed 2026](history_seed_2026.csv)
- [UNet++ seed 9999 (лучший)](history_seed_9999_unet.csv)
- [UNet++ seed 42](history_seed_0042_unet.csv)
- [UNet++ seed 2026](history_seed_2026_unet.csv)
- [Сводная статистика](all_models_summary.csv)

## Графики обучения

### Сравнение моделей (UNet++ vs FPN)

+

### Сравнение Validation Loss, Dice, IoU по всем сидам

+

### Train/Validation Loss по каждому сиду

| Seed 42 | Seed 9999 | Seed 2026 |
|---------|-----------|-----------|
| ![Loss 42](loss_curves_seed_0042.png) | ![Loss 9999](loss_curves_seed_9999.png) | ![Loss 2026](loss_curves_seed_2026.png) |

### Сравнение Loss всех сидов

+

## Ссылка на submission 

https://drive.google.com/drive/folders/1ASyMmN1MuM6A88Hf06OZ2NU0pUnjlbBz

## Код

(https://drive.google.com/drive/folders/1nMgl88w9Gb6eaP3c7zxd2zfkArYiyESK?usp=drive_link)
