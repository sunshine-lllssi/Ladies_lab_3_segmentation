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


## Графики обучения
![Color Ablation](https://github.com/sunshine-lllssi/Ladies_lab_3_segmentation/blob/main/Best_code/loss_curves_seed_FPN_0042.png)
![Color Ablation](https://github.com/sunshine-lllssi/Ladies_lab_3_segmentation/blob/main/Best_code/loss_curves_seed_FPN_2026.png)
![Color Ablation](https://github.com/sunshine-lllssi/Ladies_lab_3_segmentation/blob/main/Best_code/loss_curves_seed_FPN_9999.png)
![Color Ablation](https://github.com/sunshine-lllssi/Ladies_lab_3_segmentation/blob/main/Best_code/loss_curves_seed_UnetPlusPlus_0042.png)
![Color Ablation](https://github.com/sunshine-lllssi/Ladies_lab_3_segmentation/blob/main/Best_code/loss_curves_seed_UnetPlusPlus_2026.png)
![Color Ablation](https://github.com/sunshine-lllssi/Ladies_lab_3_segmentation/blob/main/Best_code/loss_curves_seed_UnetPlusPlus_9999.png)
### Сравнение моделей (UNet++ vs FPN)
![Color Ablation](https://github.com/sunshine-lllssi/Ladies_lab_3_segmentation/blob/main/Best_code/Снимок%20экрана%202026-04-10%20232657.png)
![Color Ablation](https://github.com/sunshine-lllssi/Ladies_lab_3_segmentation/blob/main/Best_code/Снимок%20экрана%202026-04-10%20232710.png)

UNet++:
  Лучший Val Dice: 0.9120 (эпоха 39)
  Лучший Val IoU: 0.8505

FPN:
  Лучший Val Dice: 0.9164 (эпоха 67)
  Лучший Val IoU: 0.8590



### Сравнение Loss всех сидов

![Color Ablation](https://github.com/sunshine-lllssi/Ladies_lab_3_segmentation/blob/main/Best_code/Снимок%20экрана%202026-04-10%20233129.png)

## Ссылка на submission 

https://drive.google.com/drive/folders/1ASyMmN1MuM6A88Hf06OZ2NU0pUnjlbBz

## Код

(https://drive.google.com/drive/folders/1nMgl88w9Gb6eaP3c7zxd2zfkArYiyESK?usp=drive_link)
