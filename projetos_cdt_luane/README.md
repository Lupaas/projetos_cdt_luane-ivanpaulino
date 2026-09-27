# 🤖 Automação de Mensagem no WhatsApp Web

Este projeto é um **bot de automação desenvolvido em Python** que utiliza o **Selenium WebDriver** para acessar o WhatsApp Web, localizar um grupo específico, mencionar um usuário e enviar a mensagem automaticamente.

O projeto foi desenvolvido com o objetivo de praticar conceitos de **automação de tarefas, interação com páginas web, manipulação de teclado e localização de elementos HTML utilizando Python e Selenium**.

---

## 📌 Funcionalidades

O bot realiza automaticamente as seguintes etapas:

* 🌐 Abre o Google Chrome;
* 💬 Acessa o WhatsApp Web;
* ⏳ Aguarda o carregamento da página;
* 🔎 Utiliza o atalho de pesquisa do WhatsApp Web;
* 👥 Localiza um grupo específico;
* ✍️ Digita uma menção utilizando `@`;
* ✅ Confirma o usuário mencionado;
* 📤 Envia a mensagem;
* ⚠️ Exibe uma mensagem detalhada caso ocorra algum erro.

---

## 🛠️ Tecnologias utilizadas

* **Python**
* **Selenium**
* **Google Chrome**
* **ChromeDriver**
* **WhatsApp Web**

### Bibliotecas Python

```python
import time

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.action_chains import ActionChains
```

---

## ⚙️ Como funciona

O funcionamento do projeto pode ser dividido em algumas etapas.

### 1. Configuração do Chrome

O Selenium é configurado para utilizar um perfil separado do Chrome:

```python
chrome_options = Options()
chrome_options.add_experimental_option("detach", True)
chrome_options.add_argument(
    r"--user-data-dir=C:\Users\Aluno\Desktop\PerfilChromeBot"
)
```

O perfil separado permite que o navegador utilizado pelo bot mantenha seus próprios dados de sessão.

---

### 2. Acesso ao WhatsApp Web

Depois da configuração, o Selenium inicia o navegador e acessa:

```python
driver = webdriver.Chrome(options=chrome_options)

driver.get("https://web.whatsapp.com")
```

O programa aguarda alguns segundos para permitir que o WhatsApp Web seja carregado.

```python
time.sleep(15)
```

---

### 3. Localização do grupo

O projeto utiliza `ActionChains` para simular ações do teclado.

```python
actions = ActionChains(driver)

actions.key_down(Keys.CONTROL)\
       .key_down(Keys.ALT)\
       .send_keys("/")\
       .key_up(Keys.ALT)\
       .key_up(Keys.CONTROL)\
       .perform()
```

Depois disso, o bot digita o nome do grupo:

```python
actions.send_keys("Programação 2/26 B/Tarde").perform()
```

E pressiona `Enter` para acessar a conversa.

---

### 4. Menção do usuário

Após abrir o grupo, o bot digita a menção:

```python
actions.send_keys("@luanepenafort").perform()
```

Em seguida, pressiona `Enter` para selecionar a pessoa na lista de sugestões.

---

### 5. Envio da mensagem

Por fim, o Selenium procura o botão de envio utilizando XPath:

```python
send_button = driver.find_element(
    By.XPATH,
    '//button[@aria-label="Enviar" or @data-tab="11"]'
)

send_button.click()
```

Se tudo ocorrer corretamente, o programa exibe:

```text
Mensagem enviada com sucesso!
```

---

## 🚀 Como executar o projeto

### 1. Instale o Python

É necessário ter o **Python 3** instalado no computador.

Para verificar:

```bash
python --version
```

---

### 2. Instale o Selenium

No terminal, execute:

```bash
pip install selenium
```

---

### 3. Configure o perfil do Chrome

No código, altere o caminho abaixo para uma pasta existente no seu computador:

```python
chrome_options.add_argument(
    r"--user-data-dir=C:\Users\Aluno\Desktop\PerfilChromeBot"
)
```

**Importante:** o caminho deve ser válido para o computador onde o projeto será executado.

---

### 4. Execute o programa

No terminal:

```bash
python nome_do_arquivo.py
```

O Google Chrome será aberto automaticamente e o bot acessará o WhatsApp Web.

---

## 🔐 Primeiro acesso

Na primeira execução, pode ser necessário realizar a autenticação no WhatsApp Web utilizando o **QR Code**.

Depois que a sessão estiver configurada no perfil utilizado pelo Selenium, o navegador poderá reutilizar essa sessão nas próximas execuções, desde que ela continue válida.

---

## 📂 Estrutura do projeto

Uma estrutura simples pode ser:

```text
automacao-whatsapp/
│
├── bot_whatsapp.py
└── README.md
```

---

## ⚠️ Observações

Este projeto depende da interface atual do WhatsApp Web. Alterações nos elementos, atalhos, atributos ou estrutura da página podem fazer com que a automação deixe de funcionar.

O projeto também utiliza tempos de espera fixos com `time.sleep()`, portanto o funcionamento pode variar de acordo com a velocidade da conexão e do computador.

Além disso, o uso de automações no WhatsApp deve respeitar as regras e políticas aplicáveis à plataforma.

---

## 🎯 Objetivo educacional

Este projeto foi desenvolvido principalmente para praticar:

* Automação de tarefas;
* Python;
* Selenium WebDriver;
* Manipulação de teclado;
* `ActionChains`;
* Localização de elementos com XPath;
* Tratamento de exceções;
* Interação automatizada com páginas web.

---

## 👩‍💻 Projeto

**Projeto de Automação WhatsApp Web**

Desenvolvido para fins de estudo e prática de **Python e automação web**.
