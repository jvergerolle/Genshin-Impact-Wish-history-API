# Genshin Impact Wish History Web API

---

### Get wish history (JSON)

```jsx
https://hk4e-api-os.mihoyo.com/event/gacha_info/api/getGachaLog?authkey_ver=1&sign_type=2&auth_appid=webview_gacha&init_type=301&lang=en&authkey=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX&gacha_type=301&page=1&size=6&end_id=0
```

**Base URL** : https://hk4e-api-os.mihoyo.com/event/gacha_info/api/getGachaLog

**Params**

- authkey_ver=1 `mandatory`
- sign_type=2 `mandatory`
- auth_appid=webview_gatcha
- init_type=*gatcha code number* `mandatory`
    - 100 = begginer banner
    - 200 = permanent banner
    - 301 = character event banner
    - 302 = weapon event banner
- lang=*country code* `mandatory` (Same lang code as the game)
    - en = English
    - fr = French
- authkey=*urlencoded* *key* `mandatory` *(vary with time can be obtained from the game or external pages fetch by the game)*
- gatcha_type=*gatcha code number* `mandatory`
    - 100 = begginer banner
    - 200 = permanent banner
    - 301 = event banner
    - 302 = weapon banner
- page=*page number* `mandatory`
- size=*array size (between 1 and 20 / default 6)*
- end_id = *last wish id in the previous page (can be 0 to get first page)*

### **Returned JSON example**

```json
{
  "retcode": 0,
  "message": "OK",
  "data": {
    "page": "1",
    "size": "6",
    "total": "0",
    "list": [
      {
        "uid": "710805498",
        "gacha_type": "301",
        "item_id": "",
        "count": "1",
        "time": "2021-03-02 18:48:40",
        "name": "Hu Tao",
        "lang": "en-us",
        "item_type": "Character",
        "rank_type": "5",
        "id": "1614704760008110546"
      },
      {
        "uid": "710805498",
        "gacha_type": "301",
        "item_id": "",
        "count": "1",
        "time": "2021-03-02 18:48:12",
        "name": "Ferrous Shadow",
        "lang": "en-us",
        "item_type": "Weapon",
        "rank_type": "3",
        "id": "1614704760008079589"
      },
      {
        "uid": "710805498",
        "gacha_type": "301",
        "item_id": "",
        "count": "1",
        "time": "2021-03-02 18:47:41",
        "name": "Raven Bow",
        "lang": "en-us",
        "item_type": "Weapon",
        "rank_type": "3",
        "id": "1614704760008045229"
      },
      {
        "uid": "710805498",
        "gacha_type": "301",
        "item_id": "",
        "count": "1",
        "time": "2021-03-02 18:47:41",
        "name": "Bloodtainted Greatsword",
        "lang": "en-us",
        "item_type": "Weapon",
        "rank_type": "3",
        "id": "1614704760008045228"
      },
      {
        "uid": "710805498",
        "gacha_type": "301",
        "item_id": "",
        "count": "1",
        "time": "2021-03-02 18:47:41",
        "name": "Raven Bow",
        "lang": "en-us",
        "item_type": "Weapon",
        "rank_type": "3",
        "id": "1614704760008045227"
      },
      {
        "uid": "710805498",
        "gacha_type": "301",
        "item_id": "",
        "count": "1",
        "time": "2021-03-02 18:47:41",
        "name": "Chongyun",
        "lang": "en-us",
        "item_type": "Character",
        "rank_type": "4",
        "id": "1614704760008045226"
      }
    ],
    "region": "os_euro"
  }
}
```
## Updates

### Update February 2021 
`item_id` is no longer filled in response

### Update 1.4 (March 2021)
Mihoyo has changed the pagination mechanic. They added an `id` for each wish and a parameter `end_id` in the url. To get the wishes in a page you need to provide the last wish id from the previous page in the `end_id` parameter. If you do not provide a valid `end_id` or `end_id` is missing the API will return the first page.

### Update 2.3 (November 2021)
- Mihoyo has changed the authentication method to request the API. The authkey to get wish data must be from the webview_gatcha app (wish history page) in order to get the wish history.
- The value of key `gacha_type` can now be 301 or 400. (**301** will be for wishes made on "Character event wish" banners and **400** will be for "Character event wish - 2".)
