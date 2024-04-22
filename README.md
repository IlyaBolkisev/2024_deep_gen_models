# Обучение Stable diffusion 1.5 методом Dreambooth

Необходимо дообучить модель Stable Diffusion на генерацию изображений конеретного человека. Также необходимо обучить модель LoRA и провести эксперименты по подбору параметра --rank. Обученные модели нужно объединить в один конвеер с одной из вариаций ControlNet и получить предсказания.   <br />

# Датасет

Датасет из 18 изображений актрисы Эммы Уотсон 512х512 (./imgs) <br />

<p>
<img src="imgs/1__17_.jpeg.bf53993c9b93a28409302423f1e44cfc.jpeg" alt="example1" width="300" />
<img src="imgs/6426dd3add25f618469340.jpg" alt="example2" width="300" />
<img src="imgs/gettyimages-1347087545-1-scaled-e1634546294376.jpg" alt="example3" width="300" />
</p>

# Эксперименты

## Обучение Unet
loss = 0.0463 <br />
<img src="report_images/base_model/street.jpg" alt="example1" width="300" />
<img src="report_images/base_model/football.jpg" alt="example1" width="300" />


## Обучение LoRA
### Rank 32
loss = 0.785 <br />
<img src="report_images/lora_r32/kitchen.jpg" alt="example1" width="300" />
<img src="report_images/lora_r32/street.jpg" alt="example1" width="300" />

### Rank 64
loss = 0.0707 <br />
<img src="report_images/lora_r64/office.jpg" alt="example1" width="300" />
<img src="report_images/lora_r64/football.jpg" alt="example1" width="300" />

### Rank 128
loss = 0.422 <br />
<img src="report_images/lora_r128/street.jpg" alt="example1" width="300" />
<img src="report_images/lora_r128/forest.jpg" alt="example1" width="300" />

## ControlNet
### Unet
<img src="report_images/control_net_pose/base.png" alt="example1" width="300" />

### LoRA r32
<img src="report_images/control_net_pose/lora_r64.png" alt="example1" width="300" />

# Сравнение Unet и LoRA 
Лучшую модель LoRA (r64) я отобрал по значению функции потерь. <br />

## Football
<img src="report_images/base_model/football.jpg" alt="example1" width="300" />
<img src="report_images/lora_r64/football.jpg" alt="example1" width="300" />

## Forest
<img src="report_images/base_model/forest.jpg" alt="example1" width="300" />
<img src="report_images/lora_r64/forest.jpg" alt="example1" width="300" />

## Kitchen
<img src="report_images/base_model/kitchen.jpg" alt="example1" width="300" />
<img src="report_images/lora_r64/kitchen.jpg" alt="example1" width="300" />

## Office
<img src="report_images/base_model/office.jpg" alt="example1" width="300" />
<img src="report_images/lora_r64/office.jpg" alt="example1" width="300" />

## Street
<img src="report_images/base_model/street.jpg" alt="example1" width="300" />
<img src="report_images/lora_r64/street.jpg" alt="example1" width="300" />

# Выводы
По значению функции потерь SD1.5 и LoRA r64 очень близки, и общее качество генерации у них на высоте, но по-моему мнению изображения сгенерированные с помощью LoRA получаются слишком яркими. <br />
По поводу ControlNet, я выбрал вариацию с нахождением границ референса. Позы получились очень похожими, но общее качество сгенерированных изображений ощутимо снизилось.

# Навигация
[Блокнот](/SD_1_5.ipynb) с процессом обучения.  <br /> 
[Папка](/report_images) с изображениями результатов <br />
Используемые библиотеки [файл](/requirements.txt)