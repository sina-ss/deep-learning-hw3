<style>
/* --- Base text --- */
body {
  direction: rtl;
  text-align: justify;
  line-height: 1.9;
  font-family: "B Nazanin", "Times New Roman", Tahoma, Arial, sans-serif;
  font-size: 16pt;
  margin: 2em;
}

/* --- Headings --- */
h1, h2, h3, h4, h5, h6 {
  direction: rtl;
  text-align: right;
  font-family: "B Nazanin", "Times New Roman", Tahoma, Arial, sans-serif;
  font-weight: bold;
  margin-top: 1.8em;
  margin-bottom: 0.6em;
  line-height: 1.4;
}

/* Academic style for different levels */
h1 {
  font-size: 24pt;
  border-bottom: 2px solid #444;
  padding-bottom: 0.3em;
  margin-bottom: 1em;
}

h2 {
  font-size: 20pt;
  border-right: 4px solid #666;
  padding-right: 0.4em;
}

h3 {
  font-size: 18pt;
  color: #222;
}

h4 {
  font-size: 16pt;
  color: #333;
  font-style: italic;
}

/* --- Lists --- */
ul, ol {
  margin-right: 2em;
  margin-left: 0;
  padding-right: 1.5em;
}

/* --- Bold & Italic --- */
strong {
  font-weight: bold;
}

em {
  font-style: italic;
}

/* --- Tables (if you add later) --- */
table {
  border-collapse: collapse;
  width: 100%;
  text-align: center;
  margin: 1em 0;
}

th, td {
  border: 1px solid #888;
  padding: 6px 10px;
}

th {
  background: #f0f0f0;
}
</style>

<p style="text-align:center; font-family:'B Nazanin', Tahoma, Arial, sans-serif; font-size:18pt; font-weight:bold;">
بسم الله الرحمن الرحیم
</p>

---

<p style="text-align:right; font-family:'B Nazanin', Tahoma, Arial, sans-serif; font-size:14pt;">
نام: سینا سپهوند  <br>
شماره دانشجویی: 4032904001
</p>

# تکلیف یادگیری عمیق ۳ – پاسخ سؤال ۱

## (الف) محدودیت‌های Transfer Learning

### چرا مدل‌های pretrained روی ImageNet ممکن است در حوزه تصویربرداری پزشکی عملکرد ضعیفی داشته باشند:

**۱. شکاف دامنه (Domain Gap)**

- ImageNet شامل تصاویر طبیعی (حیوانات، اشیاء، مناظر) است، در حالی‌که تصاویر پزشکی ویژگی‌های بصری کاملاً متفاوتی دارند.
- تصاویر پزشکی اغلب از modalityهای متفاوت (مانند X-ray، MRI، CT، histology) با توزیع شدت و نویز خاص تولید می‌شوند.
- فضای رنگی متفاوت است: ImageNet مبتنی بر RGB است، در حالی‌که تصاویر پزشکی معمولاً grayscale یا دارای mapping‌ رنگی تخصصی هستند.

**۲. عدم انطباق در بازنمایی ویژگی‌ها (Feature Representation Mismatch)**

- ویژگی‌های سطح پایین یادگرفته‌شده (مانند edges و textures) در تصاویر طبیعی الزاماً برای پزشکی کاربردی نیستند.
- ویژگی‌های سطح بالای semantic (مثل گربه، ماشین، درخت) کاملاً بی‌ارتباط با تشخیص پزشکی‌اند.
- تصاویر پزشکی نیازمند الگوهای domain-specific هستند (ساختارهای آناتومیک، نشانه‌های پاتولوژیک).

**۳. تفاوت در آمار تصاویر (Image Statistics)**

- توزیع شدت و الگوهای contrast متفاوت است.
- پروتکل‌های اخذ تصویر پزشکی استانداردسازی شده و با عکاسی طبیعی متفاوت‌اند.
- وضوح فضایی و نسبت ابعاد نیز می‌تواند تفاوت داشته باشد.

### راهکارهای بهبود:

**۱. Pretraining دامنه‌-ویژه**

- استفاده از مدل‌های pretrained روی دیتاست‌های پزشکی (مثل CheXNet برای X-ray قفسه سینه).
- در صورت وجود داده کافی، ایجاد foundation modelهای پزشکی.

**۲. Fine-tuning تدریجی (Progressive Fine-tuning)**

- ابتدا ثابت نگه‌داشتن لایه‌های اولیه و سپس آزاد کردن تدریجی لایه‌های عمیق‌تر.
- استفاده از learning rate کمتر برای لایه‌های pretrained و بیشتر برای لایه‌های جدید.
- بهره‌گیری از استراتژی unfreezing مرحله‌ای.

**۳. Data Augmentation و Domain Adaptation**

- به‌کارگیری augmentationهای مرتبط با پزشکی (چرخش، تغییر شدت، شبیه‌سازی نویز).
- استفاده از تکنیک‌های domain adaptation (مثل adversarial training).
- به‌کارگیری cyclic learning rate و regularization مناسب.

---

## (ب) لایه Fully Connected در برابر Convolutional

### کارایی پارامترها (Parameter Efficiency)

- **Convolutional Layers:** اشتراک پارامترها در ابعاد فضایی → کاهش شدید تعداد پارامترها.
- **Fully Connected Layers:** هر ورودی به هر خروجی وزن مستقل دارد → پارامترها به‌شدت زیاد.

### ریسک overfitting

- **Convolutional Layers:** به دلیل اشتراک وزن و translation invariance ریسک پایین‌تر.
- **Fully Connected Layers:** پارامتر زیاد → ریسک overfitting بالا → نیازمند regularization.

### بایاس استقرایی (Inductive Bias)

- **Convolutional Layers:** فرض محلی بودن پیکسل‌ها و translation invariance → یادگیری سلسله‌مراتبی ویژگی‌ها.
- **Fully Connected Layers:** فاقد فرض ساختاری → توانایی یادگیری نگاشت دلخواه اما نیازمند داده زیاد.

### قابلیت تفسیر

- **Convolutional Layers:** فیلترها قابل visualization → progression از edges تا الگوهای پیچیده.
- **Fully Connected Layers:** ماتریس وزن‌ها تفسیر دشوار → نیازمند تکنیک‌های attribution.

### مثال‌ها

- **Convolutional مؤثرتر:** Classification تصاویر (به دلیل ساختار مکانی و translation invariance).
- **Fully Connected مؤثرتر:** پردازش داده‌های جدولی (روابط غیرمکانی بین ویژگی‌ها).

---

## (پ) مقابله با Overfitting در شبکه‌های عمیق

### تکنیک ۱: Dropout

- **مفهوم:** غیرفعال‌سازی تصادفی درصدی از نورون‌ها در training.
- **موارد کاربرد:** لایه‌های fully connected بزرگ، دیتاست کوچک.
- **محدودیت‌ها:** کندی همگرایی، عدم کارایی در نرخ‌های بالا، تداخل با batch normalization.

### تکنیک ۲: Data Augmentation

- **مفهوم:** افزایش مصنوعی اندازه دیتاست با تبدیلاتی مثل چرخش، نویز.
- **موارد کاربرد:** وظایف vision با داده کم، نیاز به robust بودن.
- **محدودیت‌ها:** هزینه محاسباتی، ریسک تغییر برچسب، امکان واردکردن bias ناخواسته.

---

## (ت) شبکه‌های Siamese

**تعریف:**
معماری شامل دو زیرشبکه یکسان با اشتراک وزن که ورودی‌های مختلف را در فضای embedding مشترک مقایسه می‌کنند.

**مزایا در وظایف Verification:**

1. **یادگیری مستقیم شباهت:** مناسب برای وظایف same/different.
2. **توانایی Few-shot learning:** بدون نیاز به retraining برای کلاس‌های جدید.
3. **پایداری در عدم توازن کلاسی:** تمرکز روی مقایسه زوج‌ها به‌جای توزیع کلاس.

**اجزای اصلی:**

1. **Shared Feature Extractor**
2. **Distance/Similarity Metric** (مانند cosine similarity یا Euclidean distance)
3. **Loss Function** (contrastive loss، triplet loss، یا binary cross-entropy)

---

## (ث) توابع Activation

**ReLU:**

- پرکاربرد در معماری‌های مدرن (CNN، ResNet، Transformer).
- مزایا: کارایی محاسباتی، حل مشکل vanishing gradient.
- معایب: مشکل dead neuron، عدم صفر-مرکزی.

**Sigmoid:**

- مناسب برای output باینری.
- مزایا: bounded به \[0,1].
- معایب: vanishing gradient شدید، saturation.

**Tanh:**

- مناسب در RNN/LSTM و جاهایی که خروجی zero-centered مهم است.
- مزایا: خروجی در بازه \[-1,1]، بهبود جریان گرادیان.
- کاربرد در hidden stateها و بعضی normalization scenarios.
