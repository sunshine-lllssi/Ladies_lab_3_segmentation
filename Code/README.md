## Использовали:

Архитектура: U-Net++ с энкодером EfficientNet-B3 (предобучен на ImageNet)

Ансамблирование 3 моделей, обученных с разными seed :
- 9999
- 42
- 2026

## Обучение моделей

- Реализован пайплайн обучения с логированием и early stopping

- Использованы 3  seed (9999, 42, 2026) 

Лучший результат достигнут при seed=42:

- Validation Dice: 0.9197

- Validation IoU: 0.8638

Веса:
https://drive.google.com/drive/folders/1-cLjAVSxjW8YMljtZmT4kwbDoRuz7l6Q?usp=drive_link

## Визуализация 
![Color Ablation](https://raw.githubusercontent.com/sunshine-lllssi/Ladis_lab_2_detection/main/Снимок%20экрана%202026-03-19%20160103.png)
