# Web-scrapping con Selenium

1. Seteando Selenium y sus configuraciones:
```python
!pip install -q selenium
!apt-get -qq update
!apt-get install -qq -y chromium-browser
!apt install -qq chromium-chromedriver
from selenium import webdriver
from selenium.webdriver.common.by import By
options = webdriver.ChromeOptions()
options.add_argument('--no-sandbox')
options.add_argument('--headless')
options.add_argument('--disable-gpu')
options.add_argument('--disable-dve-shm-usage')
driver = webdriver.Chrome(options=options)
```


2. Usamos selenium
```python
# ¿A qué página queremos ir?
url=''
driver.get(url)
# ¿Qué elemento vamos a extraer?
elemento= driver.find_element(By.XPATH,"")
#recordar: By.XPATH ; By.ID ; By.CSS_SELECTOR ; By.CLASS_NAME ...
```
    

3. Extrayendo tablas (Selenium + Pandas)
```python
import pandas as pd

url=''
driver.get(url)

table_path=driver.find_element(By.XPATH,'')
table_html = table_path.get_attribute( 'innerHTML' )


header= '<table>'
table = pd.read_html(header+table_html)

tabla=table[ 0 ].iloc[ : , : ]
tabla
```

        
