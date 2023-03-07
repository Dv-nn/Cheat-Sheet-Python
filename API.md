## API  
API - application programming interface программный интерфейс приложения.
Все API-интерфейсы работают приблизительно одинаково. Обычно программа-клиент запрашивает информацию или данные, а API возвращает ответ в соответствии с тем, что мы запросили.

****SOAP vs REST vs GraphQL****

1. SOAP (Simple Object Access Protocol) ассоциируется с корпоративным миром, имеет строгую систему на основе «контрактов». Этот подход в основном связан скорее с обработкой действий, чем с данными.
2. REST (Representational State Transfer) используется для общедоступных API и идеально подходит для получения данных из интернета.
3. GraphQL -  созданный Facebook гибкий язык API-запросов

- `request` содержит данные запроса API: базовый URL, конечную точку, используемый метод, заголовки и т. д.
- `response` содержит соответствующие данные, возвращаемые сервером, в том числе контент, код состояния и заголовки.

```python
import requests

response = requests.get("https://randomuser.me/api/")
response.text

'{
    "results": [
    {
        "gender": "female",
        "name":
        {
            "title": "Mrs",
            "first": "Britt",
            "last": "Ludwig"
        },
        "location":
        {
            "street":>..}
		}
	]
}
```

### **Заголовки HTTP**

HTTP-заголовки (headers) используются для определения нескольких параметров, управляющих запросами и ответами:

| HTTP Header | Описание |
| --- | --- |
| Accept | Какой тип контента может принять клиент |
| Content-Type | Какой тип контента в ответе сервера |
| User-Agent | Какое программное обеспечение клиент использует для связи с сервером |
| Server | Какое программное обеспечение сервер использует для связи с клиентом |
| Authentication | Кто вызывает API и с какими учетными данными |

### Ключ API

Самый распространенный подход к аутентификации — это ключ API (API key). Эти ключи используются для идентификации вас как пользователя или клиента API, а также для отслеживания использования вами интерфейса.

### ****OAuth****

Когда приложение или платформа позволяет зарегистрироваться или войти с помощью другого ресурса,  поток аутенфикации обычно использует OAuth.

Что происходит, когда мы нажимаем в приложении кнопку «Продолжить с Vk»:

1. Приложение  запрашивает API Vk запустить процесс аутентификации. Для этого приложение  отправит идентификатор приложения (`client_id`) и URL-адрес (`redirect_uri`) для перенаправления пользователя после взаимодействия с API Vk.
2. Клиент будет перенаправлен на сайт Vk, где нас попросят войти в систему с учетными данными. Приложение  **не увидит** эти учетные данные и **не получит к ним доступа**. Это самое важное преимущество OAuth.
3. Vk отобразит данные профиля, запрашиваемые приложением, и попросит принять или отклонить обмен этими данными.
4. Если вы согласитесь предоставить приложению доступ к своим данным, вы будете перенаправлены обратно в приложение и получите доступ к системе. Vk предоставит  приложению специальные учетные данные — токен доступа (`access_token`), который можно многократно использовать для получения информации.

Вот что нам нужно знать при использовании API с использованием OAuth:

- Нам нужно создать приложение, которое будет иметь идентификатор (`app_id` или `client_id`) и некоторую секретную строку (`app_secret` или `client_secret`).
- У нас должен быть URL-адрес перенаправления (`redirect_uri`), который API будет использовать для отправки нам информации.
- В результате аутентификации мы получим код (`exchange_code`), который необходимо обменять на токен доступа (`access_token`).

```python
import requests

# Замените следующие переменные вашим Client ID и Client Secret
CLIENT_ID = "<REPLACE_WITH_CLIENT_ID>"
CLIENT_SECRET = "<REPLACE_WITH_CLIENT_SECRET>"

# Замените значение переменной с помощью url, указанного вами
# в поле "Authorization callback URL"
REDIRECT_URI = "<REPLACE_WITH_REDIRECT_URI>"

def create_oauth_link():
    params = {
        "client_id": CLIENT_ID,
        "redirect_uri": REDIRECT_URI,
        "scope": "user",
        "response_type": "code",
    }
    endpoint = "https://github.com/login/oauth/authorize"
    response = requests.get(endpoint, params=params)
    url = response.url
    return url

def exchange_code_for_access_token(code=None):
    params = {
        "client_id": CLIENT_ID,
        "client_secret": CLIENT_SECRET,
        "redirect_uri": REDIRECT_URI,
        "code": code,
    }
    headers = {"Accept": "application/json"}
    endpoint = "https://github.com/login/oauth/access_token"
    response = requests.post(endpoint, params=params, headers=headers).json()
    return response["access_token"]

def print_user_info(access_token=None):
    headers = {"Authorization": f"token {access_token}"}
    endpoint = "https://api.github.com/user"
    response = requests.get(endpoint, headers=headers).json()
    name = response["name"]
    username = response["login"]
    private_repos_count = response["total_private_repos"]
    print(
        f"{name} ({username}) | private repositories: {private_repos_count}"
    )

link = create_oauth_link()
print(f"Follow the link to start the authentication with GitHub: {link}")
code = input("GitHub code: ")
access_token = exchange_code_for_access_token(code)
print(f"Exchanged code {code} и access token: {access_token}")
print_user_info(access_token=access_token)
```

---

### **REST API**

 **-**  это архитектурный подход, который устанавливает ограничения для API: как они должны быть устроены и какие функции поддерживать. Это позволяет стандартизировать работу программных интерфейсов, сделать их более удобными и производительными.

REST **6 принципов архитектуры**

Всего в REST есть шесть требований к проектированию API. Пять из них обязательные, одно — опциональное:

- Клиент-серверная модель (client-server model).
- Отсутствие состояния (statelessness).
- Кэширование (cacheability).
- Единообразие интерфейса (uniform interface).
- Многоуровневая система (layered system).
- Код по требованию (code on demand) — необязательно.

**REST и RESTful - в чём разница?**

Термин RESTful был введён, чтобы различать сервисы, построенные чётко по шести указанным выше требованиям, от тех, которые соблюдают только часть  требований.

RESTful - это приложение, в котором соблюдаются все требования к построению архитектуры REST API. 

Ниже представлены основные этапы запроса REST API:

- Клиент отправляет запрос на сервер. Руководствуясь документацией API, клиент форматирует запрос таким образом, чтобы его понимал сервер.
- Сервер аутентифицирует клиента и подтверждает, что клиент имеет право сделать этот запрос.
- Сервер получает запрос и внутренне обрабатывает его.
- Сервер возвращает ответ клиенту. Ответ содержит информацию, которая сообщает клиенту, был ли запрос успешным. Также запрос включает сведения, запрошенные клиентом.
- Сведения о запросе и ответе REST API могут немного различаться в зависимости от того, как разработчики проектируют API.
