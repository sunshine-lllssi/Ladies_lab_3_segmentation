# Лучший результат на public
- 0.91837
  
- ## Результаты

- **Лучший сид (seed):** 42
- **Лучший Validation Dice:** 0.9197 (эпоха 62)
- **Лучший Validation IoU:** 0.8638 (эпоха 79)

## Модель

- **Архитектура:** UnetPlusPlus
- **Энкодер:** timm-efficientnet-b3
- **Предобучение:** ImageNet

## Обучение

Мы обучили модель сегментации на трех различных сидах (2026, 9999, 0042). Лучшие результаты показал seed = **42**.

**Параметры обучения:**
- Эпох: 85
- Размер батча: 4
- Размер изображения: 512x512
- Оптимизатор: AdamW (LR=3e-4, Weight Decay=1e-4)
- Функция потерь: Combined Loss (BCE + Dice)
- Планировщик LR: ReduceLROnPlateau
- Аугментация: HorizontalFlip, VerticalFlip, RandomRotate90


## Таблицы с метриками по эпохам

## Лучшие метрики по каждому сиду

| Seed | Лучший Dice | Эпоха | Лучший IoU | Лучший Loss |
|------|-------------|-------|------------|-------------|
| 0042 | 0.9197 | 62 | 0.8638 | 0.0681 |
| 9999 | 0.9126 | 55 | 0.8513 | 0.0641 |
| 2026 | 0.9084 | 50 | 0.8501 | 0.0719 |


## Веса моделей:
https://drive.google.com/drive/folders/1-cLjAVSxjW8YMljtZmT4kwbDoRuz7l6Q?usp=drive_link

## Визуализация обучения
![Color Ablation](https://github.com/sunshine-lllssi/Ladies_lab_3_segmentation/blob/main/Code/Снимок%20экрана%202026-04-10%20222445.png)
![Color Ablation](https://github.com/sunshine-lllssi/Ladies_lab_3_segmentation/blob/main/Code/Снимок%20экрана%202026-04-10%20222517.png)
![Color Ablation](https://github.com/sunshine-lllssi/Ladies_lab_3_segmentation/blob/main/Code/Снимок%20экрана%202026-04-10%20222527.png)

## Ссылка на submission
https://drive.google.com/file/d/1z01q4i3fehAabqAuxaJ5ddWjzAWtFdmj/view?usp=drive_link
