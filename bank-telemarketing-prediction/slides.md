---
# try also 'default' to start simple
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://images.unsplash.com/photo-1525182008055-f88b95ff7980?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MXwxfDB8MXxhbGx8fHx8fHx8fA&ixlib=rb-1.2.1&q=80&w=1080&utm_source=unsplash_source&utm_medium=referral&utm_campaign=api-credit
# apply any windi css classes to the current slide
class: "text-center"
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
    ## Slidev Starter Template
    Presentation slides for developers.

    Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
    persist: false
---

# Bank Telemarketing Analysis

A Data-Driven Approach to Predict the Success of Bank Telemarketing.

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<!-- <div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div> -->

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

<div
  v-if="$slidev.nav.currentPage === 2"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Tentang Data</h1>
</div>
<ul>
    <li>Berasal dari sebuah paper berjudul "A data-driven approach to predict the success of bank telemarketing"</li>
    <li>Penelitian dilakukan di Portugal dan dipublish pada tahun 2014</li>
    <li>
      Memiliki 20 <em>Features:</em>
      <ul>
          <li>10 <em>Numerics</em></li>
          <li>10 <em>Categorical</em></li>
      </ul>
    </li>
</ul>

<br>
<br>

<div
  v-if="$slidev.nav.currentPage === 2"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Tujuan</h1>
</div>
<ul>
    <li>Pemodelan Machine Learning bertujuan untuk memprediksi <br> apakah customer akan <em>subscribe</em> produk deposito</li>
</ul>

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>

---

<div
  v-if="$slidev.nav.currentPage === 3"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Data Features (1)</h1>
</div>

<!-- Hover on the bottom-left corner to see the navigation's controls panel, [learn more](https://sli.dev/guide/navigation.html)

### Keyboard Shortcuts -->

| Client Data                                                         | Last Contact                                  |
| ------------------------------------------------------------------- | --------------------------------------------- |
| Age 🔢                                                              | Contact 🔠 <small>cellular, telephone</small> |
| Job 🔠 <small>6 values</small>                                      | Month 🔠 <small>Jan ... Dec</small>           |
| Marital 🔠 <small>divorced, married, single</small>                 | Day of Week 🔠 <small>Mon ... Fri</small>     |
| Education 🔠 <small>8 values</small>                                | Duration 🔢💡                                 |
| Default 🔠 <small>has credit in default? (no, yes, unknown)</small> |                                               |
| Housing Loan 🔠 <small>no, yes, unknown</small>                     |                                               |
| Personal Loan 🔠 <small>no, yes, unknown</small>                    |                                               |

```
💡 Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no').
Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known.
Thus, this input should only be included for benchmark purposes and should be discarded if the intention is
to have a realistic predictive model.
```

<!-- https://sli.dev/guide/animations.html#click-animations -->
<!-- <img
  v-click
  class="absolute -bottom-9 -left-7 w-80 opacity-50"
  src="https://sli.dev/assets/arrow-bottom-left.svg"
/>
<p v-after class="absolute bottom-23 left-45 opacity-30 transform -rotate-10">Here!</p> -->

<style>
  h1 {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
</style>

---

<div
  v-if="$slidev.nav.currentPage === 4"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Data Features (2)</h1>
</div>

| Other <br> Attributes                                     | Social and Economic <br> Context Attributes |
| --------------------------------------------------------- | ------------------------------------------- |
| Campaign 🔢                                               | emp.var.rate 🔢 <small>quarterly</small>    |
| P-days 🔢                                                 | cons.price.idx 🔢 <small>monthly</small>    |
| Previous 🔢                                               | cons.conf.idx 🔢 <small>monthly</small>     |
| P-outcome 🔠 <small>failure, nonexistent, success</small> | euribor3m 🔢 <small>daily</small>           |
|                                                           | nr.employed 🔢 <small>quarterly</small>     |

<style>
  h1 {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
</style>

---
layout: two-cols

---

<div
  v-if="$slidev.nav.currentPage === 5"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Target</h1>
</div>

-   Subscribe to term deposit?
-   y = (yes/no)
- Terlihat data yang tidak seimbang pada grafik di sebelah

::right::

<br>
<br>
<br>
<br>
<br>
<img style="margin-left:70px;" border="rounded" src="/images/y_percent.png" width="300">

<style>
  h1 {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
</style>

---
layout: two-cols

---

<div
  v-if="$slidev.nav.currentPage === 6"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Analisis Deskriptif</h1>
</div>

```python {all|1-4|1-9|all}
def plot_graphs(col, df):
    # Set Figsize
    fig, ax = plt.subplots(2, sharex=True, figsize=(10, 10))

    # Plot Histogram
    sns.countplot(data=df, x=col, ax=ax[0], color='C0')
    for i, p in enumerate(ax[0].patches):
        ax[0].annotate(f'{p.get_height()}', (p.get_x()+0.1, p.get_height()+5))
    ax[0].set_title(f"{col.title()} Histogram")

    # Plot y distribution on feature
    Y = df[col]
    total = len(Y)
    sns.countplot(x=col, data=df, hue="y")
    for i, p in enumerate(ax[1].patches):
        percent = (p.get_height() / total) * 100
        ax[1].annotate(f'{percent:.2f}%', (p.get_x()+0.1, p.get_height()+5))

    ax[1].set_yticklabels(map('{:.1f}%'.format, 100*ax[1].yaxis.get_majorticklocs()/total))
    ax[1].set_xticklabels(ax[1].get_xticklabels(), rotation=10, ha="right")
    ax[1].set_title(f"y distribution on {col.title()}")
    plt.show()
```

::right::

#### Feature Type: Categorical

###### 1. Job

<small>Admin Job terlihat paling banyak subscribe dan tidak subscribe deposito</small>
<img border="rounded" src="/images/hist_job.png" width="400">


<style>
  h1 {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
</style>

---
layout: two-cols

---

#### Feature Type: Categorical

###### 2. Marital Status

<img border="rounded" src="/images/hist_marital.png" width="400">
<br>
<small>Mayoritas customer sudah menikah</small>

::right::

#### \_\_\_

###### 3. Education

<img border="rounded" src="/images/hist_education.png" width="400">

---
layout: two-cols

---

#### Feature Type: Categorical

###### 4. Default

<img style="margin-left:40px;" border="rounded" src="/images/hist_default.png" width="400">

::right::

#### \_\_\_

###### 5. housing Loan

<img style="margin-left:40px;" border="rounded" src="/images/hist_housing.png" width="400">

---
layout: two-cols

---

#### Feature Type: Categorical

###### 6. Personal Loan

<img style="margin-left:40px;" border="rounded" src="/images/hist_loan.png" width="400">

::right::

#### \_\_\_

###### 7. Contact

<img style="margin-left:40px;" border="rounded" src="/images/hist_contact.png" width="400">

---
layout: two-cols

---

#### Feature Type: Categorical

###### 8. Month

<img style="margin-left:40px;" border="rounded" src="/images/hist_month.png" width="400">

::right::

#### \_\_\_

###### 9. Day of Week

<img style="margin-left:40px;" border="rounded" src="/images/hist_day_of_week.png" width="400">

---
layout: two-cols

---

#### Feature Type: Categorical

###### 10. P-outcome

<img style="margin-left:40px;" border="rounded" src="/images/hist_poutcome.png" width="400">
<br>
<small>Terdapat nilai success yang lebih besar pada variable ini, yaitu pada customer yang sukses pada campaign sebelumnya.</small>

::right::

---
layout: two-cols

---

<div
  v-if="$slidev.nav.currentPage === 12"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Analisis Deskriptif (2)</h1>
</div>

```python
def plot_numeric_graphs(col, df):
    fig, ax = plt.subplots(2, figsize=(7, 10))
    sns.boxplot(x='y', y=col, data=df, ax=ax[0])
    sns.histplot(df[col], kde=True)
    plt.show()
```
<br>
<small>Mayoritas customer berada pada usia 30-40 tahun.</small>
::right::

#### Feature Type: Numeric

###### 1. Age

<img border="rounded" src="/images/hist_age.png" width="325">

<style>
  h1 {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
</style>

---
layout: two-cols

---

#### Feature Type: Numeric

###### 2. Duration
<small>Beda nilai median yang signifikan.</small>
<img border="rounded" src="/images/hist_duration.png" width="300">

::right::

#### \_\_\_

###### 3. Campaign

<img border="rounded" src="/images/hist_campaign.png" width="325">

---
layout: two-cols

---

#### Feature Type: Numeric

###### 4. P-days

<img border="rounded" src="/images/hist_pdays.png" width="325">

::right::

#### \_\_\_

###### 5. Previous

<img border="rounded" src="/images/hist_previous.png" width="325">

---
layout: two-cols

---

#### Feature Type: Numeric

###### 6. emp.var.rate
<small>Beda nilai median yang signifikan.</small>
<img border="rounded" src="/images/hist_emp_var_rate.png" width="300">

::right::

#### \_\_\_

###### 7. nr.employed
<small>Beda nilai median yang signifikan.</small>
<img border="rounded" src="/images/hist_nr_employed.png" width="300">

---
layout: two-cols

---

#### Feature Type: Numeric

###### 8. cons.price.idx
<small>Beda nilai median yang signifikan.</small>
<img border="rounded" src="/images/hist_cons_price_idx.png" width="300">

::right::

#### \_\_\_

###### 9. cons.conf.idx
<small>Beda nilai median yang signifikan.</small>
<img border="rounded" src="/images/hist_cons_price_idx.png" width="300">

---
layout: two-cols

---

#### Feature Type: Numeric

###### 10. euribor3m
<small>Beda nilai median yang signifikan.</small>
<img border="rounded" src="/images/hist_euribor3m.png" width="300">

::right::

#### \_\_\_

---
layout: two-cols

---

<div
  v-if="$slidev.nav.currentPage === 18"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Heat Map Correlation</h1>
</div>
<img class="ml-4" border="rounded" src="/images/heatmap_corr.png" width="475">
::right::
<br>
<br>
<small>Terdapat nilai korelasi yang tinggi pada variable `euribor3m` dan `nr.employed`.</small>
<style>
  h1 {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
</style>

---

<div
  v-if="$slidev.nav.currentPage === 19"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Preprocessing</h1>
</div>

1. Encode categorical data to dummy

```python
categorical = ['job', 'marital', 'education', 'default', 'housing', 'loan', 'contact', 'month', 'day_of_week', 'poutcome']
df_dummy = pd.get_dummies(df, columns=categorical)
df_dummy['y'] = df_dummy.y.map({'yes': 1, 'no': 0})
```

2. Split train and test data

```python
X = df_dummy.drop(columns=['y'])
y = df_dummy.y.values
X_train, X_test, y_train, y_test  = train_test_split(X, y, test_size=0.33, random_state=42)
```

<style>
  h1 {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
</style>

---
layout: two-cols

---

<div
  v-if="$slidev.nav.currentPage === 20"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Logistic Regression</h1>
</div>

##### With and Without Duration feature

```python {1-6|8-9|11-16|18-22|all}
model = LogisticRegression(class_weight='balanced', max_iter=10000)
model.fit(X_train, y_train)
y_pred = model.predict_proba(X_test)[:,1]
auc = roc_auc_score(y_test, y_pred)
print("AUC score with duration column: ", auc)
fpr, tpr, _ = roc_curve(y_test,  y_pred)

X_train_drop = X_train.drop(columns=["duration"])
X_test_drop = X_test.drop(columns=["duration"])

model = LogisticRegression(class_weight='balanced', max_iter=10000)
model.fit(X_train_drop, y_train)
y_pred_without_dur = model.predict_proba(X_test_drop)[:,1]
auc2 = roc_auc_score(y_test, y_pred_without_dur)
print("AUC score without duration column: ", auc2)
fpr2, tpr2, _ = roc_curve(y_test,  y_pred_without_dur)

plt.figure(figsize=(7,7))
plt.plot(fpr, tpr , label="Logistic, auc="+str(auc))
plt.plot(fpr2, tpr2 , label="Logistic Without Duration, auc="+str(auc2))
plt.legend(loc=4)
plt.show()
```

::right::

# \_\_\_

<img v-click class="ml-4" border="rounded" src="/images/roc_logistic.png" width="475">

<style>
  h1 {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
</style>

---
layout: two-cols

---

<div
  v-if="$slidev.nav.currentPage === 21"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Tuning Parameter</h1>
</div>

```python 
alpha = [10 ** x for x in range(-5, 4)]
auc_results = []
for a in alpha:
    model_log_reg = LogisticRegression(penalty='l2', C=a, class_weight='balanced', max_iter=10000)
    model_log_reg.fit(X_train_drop, y_train)
    y_pred = model_log_reg.predict_proba(X_test_drop)[:,1]
    auc = roc_auc_score(y_test, y_pred)
    print(f"k = {a}, AUC = {auc}")
    fpr, tpr, _ = roc_curve(y_test,  y_pred)
    plt.plot(fpr, tpr , label="Logistic, auc="+str(auc))
    plt.legend(loc=4)
    auc_results.append(roc_auc_score(y_test, y_pred))
plt.show()
best_alpha_index = np.argmax(auc_results)
best_alpha = alpha[best_alpha_index]
print(f"Best Alpha = {best_alpha}")
print(f"Best AUC Score = {auc_results[best_alpha_index]}")
```
```
Best Alpha = 0.0001
Best AUC Score = 0.7618334042855115
```

::right::

# \_\_\_

<img v-click class="ml-4" border="rounded" src="/images/multi_auc.png" width="475">

<style>
  h1 {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
</style>

---
layout: two-cols

---

<div
  v-if="$slidev.nav.currentPage === 22"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Feature Importance</h1>
</div>

###### Logistic Regression

```python 
a = 0.0001
best_model_log_reg = LogisticRegression(penalty='l2', C=a, class_weight='balanced', max_iter=10000)
best_model_log_reg.fit(X_train_drop, y_train)
y_pred = best_model_log_reg.predict_proba(X_test_drop)[:,1]

importances = abs(best_model_log_reg.coef_[0])
top_10 = np.argpartition(importances, -10)[-10:]
print("top_10", top_10)
plt.bar([x for x in range(len(importances))], importances)
plt.show()
important_features = [(t, importances[t], X_train_drop.columns[t]) for t in top_10]
print(important_features)
sorted_by_second = sorted(important_features, key=lambda tup: tup[1], reverse=True)
for s in sorted_by_second:
    print(s[2])
```
```
Top 10 features:
1. euribor3m         6. contact_cellular
2. emp.var.rate      7. contact_telephone
3. cons.price.idx    8. month_may
4. campaign          9. previous
5. age               10. cons.conf.idx
```

::right::

# \_\_\_

<img v-click class="ml-4" border="rounded" src="/images/importances.png" width="475">

<style>
  h1 {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
</style>

---
layout: two-cols

---

<div
  v-if="$slidev.nav.currentPage === 23"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Random Forest Classifier</h1>
</div>

```python 
alpha = [10, 50, 100, 500, 1000, 2000]
auc_results = []
for a in alpha:
    model_rand_forest = RandomForestClassifier(n_estimators=a, random_state=40, n_jobs=-1)
    model_rand_forest.fit(X_train_drop, y_train)
    y_pred = model_rand_forest.predict_proba(X_test_drop)[:,1]
    auc = roc_auc_score(y_test, y_pred)
    print(f"k = {a}, AUC = {auc}")
    fpr, tpr, _ = roc_curve(y_test,  y_pred)
    plt.plot(fpr, tpr , label="Random Forest, auc="+str(auc))
    plt.legend(loc=4)
    auc_results.append(roc_auc_score(y_test, y_pred))
plt.show()
best_alpha_index = np.argmax(auc_results)
best_alpha = alpha[best_alpha_index]
print(f"Best Alpha = {best_alpha}")
print(f"Best AUC Score = {auc_results[best_alpha_index]}")
```
```
Best n = 500
Best AUC Score = 0.7453327657159075
```

::right::

# \_\_\_

<img v-click class="ml-4" border="rounded" src="/images/rand_forest.png" width="475">

<style>
  h1 {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
</style>

---
layout: two-cols

---
<div
  v-if="$slidev.nav.currentPage === 24"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Feature Importance</h1>
</div>

###### Random Forest

```python 
a = 500
best_model_rand_forest = RandomForestClassifier(n_estimators=a, random_state=40, n_jobs=-1)
best_model_rand_forest.fit(X_train_drop, y_train)
y_pred = best_model_rand_forest.predict_proba(X_test_drop)[:,1]

importances = best_model_rand_forest.feature_importances_
top_10 = np.argpartition(importances, -10)[-10:]
print("top_10_index", top_10)
plt.bar([x for x in range(len(importances))], importances)
plt.show()
important_features = [(t, importances[t], X_train_drop.columns[t]) for t in top_10]
print(important_features)
sorted_by_second = sorted(important_features, key=lambda tup: tup[1], reverse=True)
for s in sorted_by_second:
    print(s[2])
```
```
Top 10 features:
1. euribor3m      6. cons.price.idx
2. age            7. emp.var.rate
3. nr.employed    8. pdays
4. campaign       9. job_admin.
5. cons.conf.idx  10. education_university.degree
```

::right::

# \_\_\_

<img v-click class="ml-4" border="rounded" src="/images/rand_forest_features.png" width="475">

<style>
  h1 {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
</style>


---

<div
  v-if="$slidev.nav.currentPage === 25"
  v-motion
  :initial="{ x: 80 }"
  :enter="{ x: 0 }">
  <h1>Rekomendasi</h1>
</div>

- Nilai AUC pada Logistic Regression lebih besar dari pada Random Forest Classification, yaitu 0.7618
- Bisa dilakukan pemodelan dengan algoritma yang lain seperti SVM atau XGBoost untuk meningkatkan nilai AUC
- Feature Importance menunjukkan bahwa variable `euribor3m` adalah yang paling signifikan dalam prediksi data ini
- Selain itu variable social/economy `emp.var.rate, cons.price.idx, cons.conf.idx, nr.employed` juga termasuk yang memberikan efek signifikan
- Variable numeric `age` dan `campaign` termasuk dalam top 5. Dapat dilakukan campaign dengan target umur tertentu untuk telemarketing selanjutnya

<style>
  h1 {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent; 
    -moz-text-fill-color: transparent;
  }
</style>

---
preload: false

---
<div class="w-60 relative mt-6">
  <div class="relative w-40 h-40">
    <img
      v-motion
      :initial="{ x: 800, y: -100, scale: 1.5, rotate: -50 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-square.png"
    />
    <img
      v-motion
      :initial="{ y: 500, x: -100, scale: 2 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-circle.png"
    />
    <img
      v-motion
      :initial="{ x: 600, y: 400, scale: 2, rotate: 100 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-triangle.png"
    />
  </div>

  <div 
    class="text-5xl absolute top-14 left-40 text-[#2B90B6] -z-1"
    v-motion
    :initial="{ x: -80, opacity: 0}"
    :enter="{ x: 0, opacity: 1, transition: { delay: 1000, duration: 500 } }">
    Terima Kasih
  </div>
</div>

<!-- vue script setup scripts can be directly used in markdown, and will only affects current page -->
<script setup lang="ts">
const final = {
  x: 0,
  y: 0,
  rotate: 0,
  scale: 1,
  transition: {
    type: 'spring',
    damping: 10,
    stiffness: 20,
    mass: 1
  }
}
</script>
