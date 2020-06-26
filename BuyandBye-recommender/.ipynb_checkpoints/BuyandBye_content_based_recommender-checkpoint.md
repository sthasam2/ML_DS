```python
import sqlite3 as lite
```


```python
conn = lite.connect("db.sqlite3")
cur = conn.cursor()
cur.execute("select * from product_item limit 5;")
```




    <sqlite3.Cursor at 0x2ae6d879ce0>




```python
results = cur.fetchall()
print (results)
```

    [(1, 'Necklace', 'NPR', 450, 'lipsum', 'item_pics/images_1.jpg', 'Brand New', 0, 'Sale', '2020-03-08 11:32:18.820751', 'necklace', 1, 1, 4, 0), (2, 'Hyundai Elantra', 'NPR', 45000, 'lipsum', 'item_pics/Edge-Of-World_Hz3Kvzo.jpg', 'Used (Worn Out)', 1, 'Sale', '2020-03-08 14:51:00.170484', 'hyundai-elantra', 1, 2, 16, 0), (3, 'Samsung Galaxy S10e', 'NPR', 55554.86, 'Samsung Galaxy S10e\r\n\r\n    Dimensions: 142.2 x 69.9 x 7.9mm, 150g, IP68\r\n    Display: 5.8-inches, 2280 x 1080 (438ppi), flat Super AMOLED\r\n    Cameras: 16MP (f/2.2) + 12MP (f/1.5 to f/2.4, AF, OIS, 4K video), 10MP front (f/1.9, AF)\r\n    Storage: 128GB or 256GB, microSD support up to 512GB\r\n    Battery: 3100mAh\r\n    Colours: Prism White, Prism Black, Prism Green, Prism Blue, Canary Yellow\r\n\r\nWe check 1,000s of prices on 1,000s of retailers to get you the lowest new price we can find. Pocket-lint may get a commission from these offers. Read more here.\r\n\r\nThe Samsung Galaxy S10e is the cheapest of the S10 range, offering a flat display and a physical fingerprint sensor, rather than a curved screen and under-display sensor. On the back, the S10e has a dual camera instead of triple.\r\n\r\nIt misses out on a couple of the latest features but the S10e still offers a new and fresh design, as well as lovely build quality and the latest hardware.', 'item_pics/3oV-ZEjkGSA.jpg', 'Brand New', 1, 'Sale', '2020-03-08 17:01:08.833604', 'samsung-galaxy-s10e', 1, 11, 150, 0), (4, 'Samsung Galaxy S10 lite', 'NPR', 45000, "Samsung Galaxy S10 Lite\r\n\r\n    Dimensions: 162.5 x 75.6 x 8.1 mm, 186g\r\n    Display: 6.7-inches, 1080 x 2400 (394ppi), Super AMOLED\r\n    Cameras: 48MP (f/2.0) + 12MP (f/2.2), 32MP front (f/2.2)\r\n    Storage: 128GB, microSD support up to 512GB\r\n    Battery: 4500mAh\r\n    Colours: Prism White, Prism Black, Prism Blue\r\n\r\nA confusing new addition to the S10 range, this new handset debuted alongside the Note 10 Lite at CES 2020 in early January. \r\n\r\nIt fits into the range above the S10e. Why? It has more cameras, a larger screen and a bigger battery. It's actually the largest of the standard S10 series, having the same screen size as the premium S10 5G. \r\n\r\nIt also has some other premium specs, not least the flagship Qualcomm Snapdragon 855 platform under the hood. Confusing, but if it debuts at the right price it will be very compelling.", 'item_pics/6lcT2kRPvnI.jpg', 'Brand New', 1, 'Sale', '2020-03-08 17:02:21.924049', 'samsung-galaxy-s10-lite', 1, 11, 150, 0), (5, 'Samsung Galaxy S10', 'NPR', 65000, "Samsung Galaxy S10\r\n\r\n    Dimensions: 149.9 x 70.4 x 7.8mm, 157g, IP68\r\n    Display: 6.1-inches, 3040 x 1440 (550ppi), dual-edge Super AMOLED\r\n    Cameras: 16MP + 12MP + 12MP (AF, OIS, 4K video), 10MP front (f/1.9, AF)\r\n    Storage: 128GB or 512GB, microSD support up to 512GB\r\n    Battery: 3400mAh\r\n    Colours: Prism White, Prism Black, Prism Green, Prism Blue\r\n\r\nWe check 1,000s of prices on 1,000s of retailers to get you the lowest new price we can find. Pocket-lint may get a commission from these offers. Read more here.\r\n\r\nThe Samsung Galaxy S10 is a great device, featuring an all-new design and plenty of new features including an in-display fingerprint sensor and reverse wireless charging.\r\n\r\nThere's a triple camera on the rear and the 19.5:9 aspect ratio display is stunning, while the software experience is up there with the best.\r\n\r\n    Samsung Galaxy S10 review", 'item_pics/o5OGVa1hfwY.jpg', 'Brand New', 1, 'Sale', '2020-03-08 17:03:12.274599', 'samsung-galaxy-s10', 1, 11, 150, 0)]
    


```python
cur.close()
conn.close()
```


```python
import pandas as pd
import sqlite3 as sq
conn=sq.connect("db.sqlite3")
```


```python
df = pd.read_sql_query("select * from product_item;", conn)
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>title</th>
      <th>price_currency</th>
      <th>price</th>
      <th>content</th>
      <th>image</th>
      <th>condition</th>
      <th>price_negotiability</th>
      <th>item_available_for</th>
      <th>date_posted</th>
      <th>slug</th>
      <th>author_id</th>
      <th>category_id</th>
      <th>sub_category_id</th>
      <th>sold</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Necklace</td>
      <td>NPR</td>
      <td>450.00</td>
      <td>lipsum</td>
      <td>item_pics/images_1.jpg</td>
      <td>Brand New</td>
      <td>0</td>
      <td>Sale</td>
      <td>2020-03-08 11:32:18.820751</td>
      <td>necklace</td>
      <td>1</td>
      <td>1</td>
      <td>4</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Hyundai Elantra</td>
      <td>NPR</td>
      <td>45000.00</td>
      <td>lipsum</td>
      <td>item_pics/Edge-Of-World_Hz3Kvzo.jpg</td>
      <td>Used (Worn Out)</td>
      <td>1</td>
      <td>Sale</td>
      <td>2020-03-08 14:51:00.170484</td>
      <td>hyundai-elantra</td>
      <td>1</td>
      <td>2</td>
      <td>16</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Samsung Galaxy S10e</td>
      <td>NPR</td>
      <td>55554.86</td>
      <td>Samsung Galaxy S10e\r\n\r\n    Dimensions: 142...</td>
      <td>item_pics/3oV-ZEjkGSA.jpg</td>
      <td>Brand New</td>
      <td>1</td>
      <td>Sale</td>
      <td>2020-03-08 17:01:08.833604</td>
      <td>samsung-galaxy-s10e</td>
      <td>1</td>
      <td>11</td>
      <td>150</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Samsung Galaxy S10 lite</td>
      <td>NPR</td>
      <td>45000.00</td>
      <td>Samsung Galaxy S10 Lite\r\n\r\n    Dimensions:...</td>
      <td>item_pics/6lcT2kRPvnI.jpg</td>
      <td>Brand New</td>
      <td>1</td>
      <td>Sale</td>
      <td>2020-03-08 17:02:21.924049</td>
      <td>samsung-galaxy-s10-lite</td>
      <td>1</td>
      <td>11</td>
      <td>150</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Samsung Galaxy S10</td>
      <td>NPR</td>
      <td>65000.00</td>
      <td>Samsung Galaxy S10\r\n\r\n    Dimensions: 149....</td>
      <td>item_pics/o5OGVa1hfwY.jpg</td>
      <td>Brand New</td>
      <td>1</td>
      <td>Sale</td>
      <td>2020-03-08 17:03:12.274599</td>
      <td>samsung-galaxy-s10</td>
      <td>1</td>
      <td>11</td>
      <td>150</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>Samsung Galaxy S10</td>
      <td>NPR</td>
      <td>75000.00</td>
      <td>Samsung Galaxy S10+\r\n\r\n    Dimensions: 157...</td>
      <td>item_pics/xGiRbMwo4Jc.jpg</td>
      <td>Brand New</td>
      <td>1</td>
      <td>Sale</td>
      <td>2020-03-08 17:03:59.627813</td>
      <td>samsung-galaxy-s10-2</td>
      <td>1</td>
      <td>11</td>
      <td>150</td>
      <td>0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>Samsung Galaxy S10 5g</td>
      <td>NPR</td>
      <td>75000.00</td>
      <td>Samsung Galaxy S10 5G\r\n\r\n    Dimensions: 1...</td>
      <td>item_pics/xGiRbMwo4Jc_NmC38Rh.jpg</td>
      <td>Brand New</td>
      <td>1</td>
      <td>Sale</td>
      <td>2020-03-08 17:05:08.309013</td>
      <td>samsung-galaxy-s10-5g</td>
      <td>1</td>
      <td>11</td>
      <td>150</td>
      <td>0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>Samsung Galaxy Note 10 lite</td>
      <td>NPR</td>
      <td>75000.00</td>
      <td>Samsung Galaxy Note 10 Lite\r\n\r\n    Dimensi...</td>
      <td>item_pics/xGiRbMwo4Jc_RnY3OaB.jpg</td>
      <td>Brand New</td>
      <td>1</td>
      <td>Sale</td>
      <td>2020-03-08 17:06:01.073486</td>
      <td>samsung-galaxy-note-10-lite</td>
      <td>1</td>
      <td>11</td>
      <td>150</td>
      <td>0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>Samsung Galaxy Note 10</td>
      <td>NPR</td>
      <td>75000.00</td>
      <td>Samsung Galaxy Note 10\r\n\r\n    Dimensions: ...</td>
      <td>item_pics/xGiRbMwo4Jc_wCyOq0E.jpg</td>
      <td>Brand New</td>
      <td>1</td>
      <td>Sale</td>
      <td>2020-03-08 17:07:08.731278</td>
      <td>samsung-galaxy-note-10</td>
      <td>1</td>
      <td>11</td>
      <td>150</td>
      <td>0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>Samsung Galaxy Note 10+</td>
      <td>NPR</td>
      <td>75000.00</td>
      <td>Samsung Galaxy Note 10+\r\n\r\n    Dimensions:...</td>
      <td>item_pics/xGiRbMwo4Jc_VWVkm8F.jpg</td>
      <td>Brand New</td>
      <td>1</td>
      <td>Sale</td>
      <td>2020-03-08 17:07:50.009908</td>
      <td>samsung-galaxy-note-10-2</td>
      <td>1</td>
      <td>11</td>
      <td>150</td>
      <td>0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>11</td>
      <td>iPhone 11 Pro</td>
      <td>NPR</td>
      <td>75000.00</td>
      <td>The iPhone 11 Pro and iPhone 11 Pro Max are sm...</td>
      <td>item_pics/xGiRbMwo4Jc_wUkNexY.jpg</td>
      <td>Brand New</td>
      <td>1</td>
      <td>Sale</td>
      <td>2020-03-08 17:13:37.481404</td>
      <td>iphone-11-pro</td>
      <td>1</td>
      <td>11</td>
      <td>150</td>
      <td>0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>12</td>
      <td>iPhone XS</td>
      <td>NPR</td>
      <td>75000.00</td>
      <td>The iPhone XS and iPhone XS Max (stylized and ...</td>
      <td>item_pics/xGiRbMwo4Jc_MV0vxqc.jpg</td>
      <td>Brand New</td>
      <td>1</td>
      <td>Sale</td>
      <td>2020-03-08 17:14:22.325624</td>
      <td>iphone-xs</td>
      <td>1</td>
      <td>11</td>
      <td>150</td>
      <td>0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>13</td>
      <td>iPhone X</td>
      <td>NPR</td>
      <td>70000.00</td>
      <td>The iPhone X (Roman numeral "X" pronounced "te...</td>
      <td>item_pics/0FwbtwEHFp0.jpg</td>
      <td>Brand New</td>
      <td>1</td>
      <td>Sale</td>
      <td>2020-03-08 17:15:22.906566</td>
      <td>iphone-x</td>
      <td>1</td>
      <td>11</td>
      <td>150</td>
      <td>0</td>
    </tr>
    <tr>
      <th>13</th>
      <td>14</td>
      <td>iPhone 8</td>
      <td>NPR</td>
      <td>70000.00</td>
      <td>The iPhone 8 and iPhone 8 Plus are smartphones...</td>
      <td>item_pics/0FwbtwEHFp0_glHk0cg.jpg</td>
      <td>Brand New</td>
      <td>1</td>
      <td>Sale</td>
      <td>2020-03-08 17:16:01.830352</td>
      <td>iphone-8</td>
      <td>1</td>
      <td>11</td>
      <td>150</td>
      <td>0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>15</td>
      <td>the alchemist</td>
      <td>NPR</td>
      <td>450.00</td>
      <td>Paulo Coelho's enchanting novel has inspired a...</td>
      <td>item_pics/18144590._SY475_.jpg</td>
      <td>Brand New</td>
      <td>0</td>
      <td>Sale</td>
      <td>2020-03-08 17:20:20.694350</td>
      <td>the-alchemist</td>
      <td>1</td>
      <td>4</td>
      <td>42</td>
      <td>0</td>
    </tr>
    <tr>
      <th>15</th>
      <td>16</td>
      <td>the alchemist</td>
      <td>NPR</td>
      <td>450.00</td>
      <td>(The Hunger Games #1)\r\nby Suzanne Collins\r\...</td>
      <td>item_pics/2767052.jpg</td>
      <td>Used (Like New)</td>
      <td>0</td>
      <td>Sale</td>
      <td>2020-03-08 17:22:55.247055</td>
      <td>the-alchemist-2</td>
      <td>1</td>
      <td>4</td>
      <td>65</td>
      <td>0</td>
    </tr>
    <tr>
      <th>16</th>
      <td>17</td>
      <td>Harry Potter and the sorcerors stone</td>
      <td>NPR</td>
      <td>450.00</td>
      <td>Harry Potter and the Sorcerer's Stone\r\n(Harr...</td>
      <td>item_pics/3._SY475_.jpg</td>
      <td>Used (Like New)</td>
      <td>0</td>
      <td>Sale</td>
      <td>2020-03-08 17:24:33.554675</td>
      <td>harry-potter-and-the-sorcerors-stone</td>
      <td>1</td>
      <td>4</td>
      <td>65</td>
      <td>0</td>
    </tr>
    <tr>
      <th>17</th>
      <td>18</td>
      <td>Hobbit</td>
      <td>NPR</td>
      <td>450.00</td>
      <td>The Hobbit, or There and Back Again\r\n(The Ho...</td>
      <td>item_pics/5907.jpg</td>
      <td>Used (Like New)</td>
      <td>0</td>
      <td>Sale</td>
      <td>2020-03-08 17:26:15.405779</td>
      <td>hobbit</td>
      <td>1</td>
      <td>4</td>
      <td>42</td>
      <td>0</td>
    </tr>
    <tr>
      <th>18</th>
      <td>19</td>
      <td>A Game of Thrones</td>
      <td>NPR</td>
      <td>450.00</td>
      <td>A Game of Thrones\r\n(A Song of Ice and Fire #...</td>
      <td>item_pics/13496.jpg</td>
      <td>Used (Like New)</td>
      <td>0</td>
      <td>Sale</td>
      <td>2020-03-08 17:28:29.107381</td>
      <td>hobbit-2</td>
      <td>1</td>
      <td>4</td>
      <td>42</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df["title"]
```




    0                                 Necklace
    1                          Hyundai Elantra
    2                      Samsung Galaxy S10e
    3                  Samsung Galaxy S10 lite
    4                       Samsung Galaxy S10
    5                       Samsung Galaxy S10
    6                    Samsung Galaxy S10 5g
    7              Samsung Galaxy Note 10 lite
    8                   Samsung Galaxy Note 10
    9                  Samsung Galaxy Note 10+
    10                           iPhone 11 Pro
    11                               iPhone XS
    12                                iPhone X
    13                                iPhone 8
    14                           the alchemist
    15                           the alchemist
    16    Harry Potter and the sorcerors stone
    17                                  Hobbit
    18                       A Game of Thrones
    Name: title, dtype: object




```python
from sklearn.feature_extraction.text import TfidfVectorizer
```


```python
from sklearn.metrics.pairwise import linear_kernel
```


```python
tf = TfidfVectorizer(analyzer='word', ngram_range=(1,3), min_df=0, stop_words='english')
```


```python
tfidf_matrix = tf.fit_transform(df['content'])
```


```python
print(tfidf_matrix)
```

      (0, 2129)	1.0
      (1, 2129)	1.0
      (2, 2819)	0.06775283776183347
      (2, 816)	0.06775283776183347
      (2, 2172)	0.06775283776183347
      (2, 1167)	0.06775283776183347
      (2, 1581)	0.06775283776183347
      (2, 2391)	0.06775283776183347
      (2, 2492)	0.06775283776183347
      (2, 3068)	0.06775283776183347
      (2, 1500)	0.06775283776183347
      (2, 2080)	0.06775283776183347
      (2, 1067)	0.06775283776183347
      (2, 2302)	0.06775283776183347
      (2, 3598)	0.06775283776183347
      (2, 1901)	0.06775283776183347
      (2, 843)	0.06775283776183347
      (2, 1328)	0.06775283776183347
      (2, 3066)	0.06775283776183347
      (2, 3164)	0.06775283776183347
      (2, 1287)	0.06775283776183347
      (2, 3113)	0.06775283776183347
      (2, 1098)	0.06775283776183347
      (2, 3156)	0.06775283776183347
      (2, 1527)	0.06775283776183347
      :	:
      (18, 1561)	0.037756409863151735
      (18, 809)	0.037756409863151735
      (18, 2112)	0.037756409863151735
      (18, 2842)	0.03109912893584192
      (18, 3017)	0.037756409863151735
      (18, 510)	0.037756409863151735
      (18, 3767)	0.07551281972630347
      (18, 3247)	0.037756409863151735
      (18, 1083)	0.03400722367326799
      (18, 1734)	0.037756409863151735
      (18, 2411)	0.037756409863151735
      (18, 2847)	0.03109912893584192
      (18, 1190)	0.03109912893584192
      (18, 2841)	0.03109912893584192
      (18, 3804)	0.037756409863151735
      (18, 3809)	0.03109912893584192
      (18, 2991)	0.028723042525505824
      (18, 3540)	0.07551281972630347
      (18, 3627)	0.037756409863151735
      (18, 2480)	0.037756409863151735
      (18, 720)	0.03109912893584192
      (18, 3404)	0.037756409863151735
      (18, 2631)	0.037756409863151735
      (18, 1680)	0.02497385633562208
      (18, 3187)	0.06801444734653599
    


```python
cosine_similarities = linear_kernel(tfidf_matrix, tfidf_matrix)
print(cosine_similarities)
```

    [[1.00000000e+00 1.00000000e+00 0.00000000e+00 0.00000000e+00
      0.00000000e+00 0.00000000e+00 0.00000000e+00 0.00000000e+00
      0.00000000e+00 0.00000000e+00 0.00000000e+00 0.00000000e+00
      0.00000000e+00 0.00000000e+00 0.00000000e+00 0.00000000e+00
      0.00000000e+00 0.00000000e+00 0.00000000e+00]
     [1.00000000e+00 1.00000000e+00 0.00000000e+00 0.00000000e+00
      0.00000000e+00 0.00000000e+00 0.00000000e+00 0.00000000e+00
      0.00000000e+00 0.00000000e+00 0.00000000e+00 0.00000000e+00
      0.00000000e+00 0.00000000e+00 0.00000000e+00 0.00000000e+00
      0.00000000e+00 0.00000000e+00 0.00000000e+00]
     [0.00000000e+00 0.00000000e+00 1.00000000e+00 1.48195494e-01
      3.38867586e-01 3.30194932e-01 1.95303039e-01 7.39138397e-02
      2.01555661e-01 1.70409318e-01 2.68173241e-03 2.00159196e-03
      1.74000279e-02 6.98195558e-03 0.00000000e+00 1.24355293e-03
      1.15647561e-03 0.00000000e+00 0.00000000e+00]
     [0.00000000e+00 0.00000000e+00 1.48195494e-01 1.00000000e+00
      1.69901937e-01 1.55643903e-01 1.49895733e-01 2.07831468e-01
      8.16671358e-02 9.38864940e-02 4.75939185e-03 1.01830252e-02
      1.58535142e-02 1.36493316e-02 0.00000000e+00 1.27340843e-03
      1.18424054e-03 1.78028893e-03 3.72842199e-03]
     [0.00000000e+00 0.00000000e+00 3.38867586e-01 1.69901937e-01
      1.00000000e+00 4.89799157e-01 3.10573386e-01 7.88175457e-02
      1.95410667e-01 2.24167949e-01 4.91999795e-03 2.67642052e-03
      1.46453995e-02 1.15251455e-02 0.00000000e+00 1.96993697e-03
      3.72129072e-03 1.38801506e-03 7.38446392e-03]
     [0.00000000e+00 0.00000000e+00 3.30194932e-01 1.55643903e-01
      4.89799157e-01 1.00000000e+00 2.77740715e-01 7.19251128e-02
      1.86354359e-01 2.20398404e-01 5.43540590e-03 4.00815682e-03
      1.46463453e-02 6.99941953e-03 0.00000000e+00 1.36569219e-03
      3.23474064e-03 1.44339744e-03 2.75021637e-03]
     [0.00000000e+00 0.00000000e+00 1.95303039e-01 1.49895733e-01
      3.10573386e-01 2.77740715e-01 1.00000000e+00 7.73619715e-02
      1.73631593e-01 2.17522174e-01 3.36858978e-03 3.49128205e-03
      1.30045100e-02 7.33826014e-03 0.00000000e+00 5.69621439e-04
      5.29734832e-04 1.20406360e-03 8.99440690e-04]
     [0.00000000e+00 0.00000000e+00 7.39138397e-02 2.07831468e-01
      7.88175457e-02 7.19251128e-02 7.73619715e-02 1.00000000e+00
      2.73104423e-01 2.25347083e-01 8.42984437e-03 1.42573188e-02
      8.33977127e-03 1.23330869e-02 0.00000000e+00 1.18177500e-03
      1.09902356e-03 9.91308474e-03 0.00000000e+00]
     [0.00000000e+00 0.00000000e+00 2.01555661e-01 8.16671358e-02
      1.95410667e-01 1.86354359e-01 1.73631593e-01 2.73104423e-01
      1.00000000e+00 4.42182737e-01 1.82924723e-02 1.19111061e-02
      1.96989167e-02 2.77120852e-03 0.00000000e+00 5.64798417e-04
      5.25249532e-04 2.11034828e-02 2.93022708e-03]
     [0.00000000e+00 0.00000000e+00 1.70409318e-01 9.38864940e-02
      2.24167949e-01 2.20398404e-01 2.17522174e-01 2.25347083e-01
      4.42182737e-01 1.00000000e+00 1.20379525e-02 1.09296374e-02
      1.81017694e-02 3.44847823e-03 0.00000000e+00 3.74320451e-03
      1.06128112e-03 1.81291996e-02 4.24227933e-03]
     [0.00000000e+00 0.00000000e+00 2.68173241e-03 4.75939185e-03
      4.91999795e-03 5.43540590e-03 3.36858978e-03 8.42984437e-03
      1.82924723e-02 1.20379525e-02 1.00000000e+00 4.20890835e-01
      2.10250048e-01 2.07467078e-01 0.00000000e+00 0.00000000e+00
      0.00000000e+00 0.00000000e+00 0.00000000e+00]
     [0.00000000e+00 0.00000000e+00 2.00159196e-03 1.01830252e-02
      2.67642052e-03 4.00815682e-03 3.49128205e-03 1.42573188e-02
      1.19111061e-02 1.09296374e-02 4.20890835e-01 1.00000000e+00
      3.09949728e-01 2.37546402e-01 0.00000000e+00 4.27585266e-04
      3.97644459e-04 0.00000000e+00 0.00000000e+00]
     [0.00000000e+00 0.00000000e+00 1.74000279e-02 1.58535142e-02
      1.46453995e-02 1.46463453e-02 1.30045100e-02 8.33977127e-03
      1.96989167e-02 1.81017694e-02 2.10250048e-01 3.09949728e-01
      1.00000000e+00 3.07402620e-01 3.25543577e-03 8.03437908e-03
      7.00543723e-03 3.62951607e-03 3.76265732e-03]
     [0.00000000e+00 0.00000000e+00 6.98195558e-03 1.36493316e-02
      1.15251455e-02 6.99941953e-03 7.33826014e-03 1.23330869e-02
      2.77120852e-03 3.44847823e-03 2.07467078e-01 2.37546402e-01
      3.07402620e-01 1.00000000e+00 0.00000000e+00 5.67506069e-04
      2.48024061e-03 0.00000000e+00 0.00000000e+00]
     [0.00000000e+00 0.00000000e+00 0.00000000e+00 0.00000000e+00
      0.00000000e+00 0.00000000e+00 0.00000000e+00 0.00000000e+00
      0.00000000e+00 0.00000000e+00 0.00000000e+00 0.00000000e+00
      3.25543577e-03 0.00000000e+00 1.00000000e+00 5.05081594e-03
      3.86325614e-03 4.95883361e-03 3.70427003e-03]
     [0.00000000e+00 0.00000000e+00 1.24355293e-03 1.27340843e-03
      1.96993697e-03 1.36569219e-03 5.69621439e-04 1.18177500e-03
      5.64798417e-04 3.74320451e-03 0.00000000e+00 4.27585266e-04
      8.03437908e-03 5.67506069e-04 5.05081594e-03 1.00000000e+00
      2.10501023e-02 1.47177719e-02 2.00003308e-02]
     [0.00000000e+00 0.00000000e+00 1.15647561e-03 1.18424054e-03
      3.72129072e-03 3.23474064e-03 5.29734832e-04 1.09902356e-03
      5.25249532e-04 1.06128112e-03 0.00000000e+00 3.97644459e-04
      7.00543723e-03 2.48024061e-03 3.86325614e-03 2.10501023e-02
      1.00000000e+00 1.78741855e-02 1.28134605e-02]
     [0.00000000e+00 0.00000000e+00 0.00000000e+00 1.78028893e-03
      1.38801506e-03 1.44339744e-03 1.20406360e-03 9.91308474e-03
      2.11034828e-02 1.81291996e-02 0.00000000e+00 0.00000000e+00
      3.62951607e-03 0.00000000e+00 4.95883361e-03 1.47177719e-02
      1.78741855e-02 1.00000000e+00 2.14111966e-02]
     [0.00000000e+00 0.00000000e+00 0.00000000e+00 3.72842199e-03
      7.38446392e-03 2.75021637e-03 8.99440690e-04 0.00000000e+00
      2.93022708e-03 4.24227933e-03 0.00000000e+00 0.00000000e+00
      3.76265732e-03 0.00000000e+00 3.70427003e-03 2.00003308e-02
      1.28134605e-02 2.14111966e-02 1.00000000e+00]]
    


```python
results = {}
print(results)
```

    {}
    


```python
for idx, row in df.iterrows():
    similar_indices = cosine_similarities[idx].argsort()[:-100:-1]
    similar_items = [(cosine_similarities[idx][i], df['id'][i]) for i in similar_indices]
    results[row['id']] = similar_items[1:]
    
# for idx, row in df.iterrows():
#     print("-----------------------------------------------------")
#     print(similar_indices)
#     print(similar_items)
#     print(results)
```


```python
def item(id):  
  return df.loc[df['id'] == id]['title'].tolist()[0].split(' - ')[0] 
```


```python
def recommend(item_id, num):
    print("Recommending " + str(num) + " products similar to " + item(item_id) + "...")   
    print("-------")
    recs = results[item_id][:num]   
    for rec in recs: 
       print("Recommended: " + item(rec[1]) + " (score:" + str(rec[0]) + ")\n______________________________________________________________________________________")
```

Basic Slicing and Indexing
Basic slicing extends Python’s basic concept of slicing to N dimensions. Basic slicing occurs when obj is a slice object (constructed by start:stop:step notation inside of brackets), an integer, or a tuple of slice objects and integers. Ellipsis and newaxis objects can be interspersed with these as well. In order to remain backward compatible with a common usage in Numeric, basic slicing is also initiated if the selection object is any non-ndarray sequence (such as a list) containing slice objects, the Ellipsis object, or the newaxis object, but not for integer arrays or other embedded sequences.

The simplest case of indexing with N integers returns an array scalar representing the corresponding item. As in Python, all indices are zero-based: for the i-th index n_i, the valid range is 0 \le n_i < d_i where d_i is the i-th element of the shape of the array. Negative indices are interpreted as counting from the end of the array (i.e., if n_i < 0, it means n_i + d_i).

All arrays generated by basic slicing are always views of the original array.

The standard rules of sequence slicing apply to basic slicing on a per-dimension basis (including using a step index). Some useful concepts to remember include:

The basic slice syntax is i:j:k where i is the starting index, j is the stopping index, and k is the step (k\neq0). This selects the m elements (in the corresponding dimension) with index values i, i + k, ..., i + (m - 1) k where m = q + (r\neq0) and q and r are the quotient and remainder obtained by dividing j - i by k: j - i = q k + r, so that i + (m - 1) k < j.

Example
>>>
>>> x = np.array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
>>> x[1:7:2]
array([1, 3, 5])
Negative i and j are interpreted as n + i and n + j where n is the number of elements in the corresponding dimension. Negative k makes stepping go towards smaller indices.

Example
>>>
>>> x[-2:10]
array([8, 9])
>>> x[-3:3:-1]
array([7, 6, 5, 4])
Assume n is the number of elements in the dimension being sliced. Then, if i is not given it defaults to 0 for k > 0 and n - 1 for k < 0 . If j is not given it defaults to n for k > 0 and -1 for k < 0 . If k is not given it defaults to 1. Note that :: is the same as : and means select all indices along this axis.

Example
>>>
>>> x[5:]
array([5, 6, 7, 8, 9])
If the number of objects in the selection tuple is less than N , then : is assumed for any subsequent dimensions.

Example
>>>
>>> x = np.array([[[1],[2],[3]], [[4],[5],[6]]])
>>> x.shape
(2, 3, 1)
>>> x[1:2]
array([[[4],
        [5],
        [6]]])
Ellipsis expand to the number of : objects needed to make a selection tuple of the same length as x.ndim. There may only be a single ellipsis present.

Example
>>>
>>> x[...,0]
array([[1, 2, 3],
       [4, 5, 6]])
Each newaxis object in the selection tuple serves to expand the dimensions of the resulting selection by one unit-length dimension. The added dimension is the position of the newaxis object in the selection tuple.

Example
>>>
>>> x[:,np.newaxis,:,:].shape
(2, 1, 3, 1)


```python
print(item(3))
recommend(3, 4)
```

    Samsung Galaxy S10e
    Recommending 4 products similar to Samsung Galaxy S10e...
    -------
    Recommended: Samsung Galaxy S10 (score:0.3388675864995107)
    ______________________________________________________________________________________
    Recommended: Samsung Galaxy S10 (score:0.3301949324341461)
    ______________________________________________________________________________________
    Recommended: Samsung Galaxy Note 10 (score:0.20155566114586354)
    ______________________________________________________________________________________
    Recommended: Samsung Galaxy S10 5g (score:0.19530303866638044)
    ______________________________________________________________________________________
    


```python
print(item(14))
recommend(14, 4)
```

    iPhone 8
    Recommending 4 products similar to iPhone 8...
    -------
    Recommended: iPhone X (score:0.3074026204845915)
    ______________________________________________________________________________________
    Recommended: iPhone XS (score:0.23754640218845505)
    ______________________________________________________________________________________
    Recommended: iPhone 11 Pro (score:0.20746707809017603)
    ______________________________________________________________________________________
    Recommended: Samsung Galaxy S10 lite (score:0.013649331648814753)
    ______________________________________________________________________________________
    


```python
print(item(18))
recommend(18, 5)
```

    Hobbit
    Recommending 5 products similar to Hobbit...
    -------
    Recommended: A Game of Thrones (score:0.021411196631731653)
    ______________________________________________________________________________________
    Recommended: Samsung Galaxy Note 10 (score:0.021103482791600448)
    ______________________________________________________________________________________
    Recommended: Samsung Galaxy Note 10+ (score:0.018129199607770763)
    ______________________________________________________________________________________
    Recommended: Harry Potter and the sorcerors stone (score:0.017874185540279745)
    ______________________________________________________________________________________
    Recommended: the alchemist (score:0.014717771902990664)
    ______________________________________________________________________________________
    


```python

```
