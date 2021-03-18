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
    - 301 = event banner
    - 302 = weapon banner
- lang=*country code* `mandatory` (Same lang code as the game)
    - en = English
    - fr = French
- authkey=*urlencoded* *key* `mandatory` *(vary with time can be obtained from the game or external pages fetch by the game)*
- gatcha_type=*gatcha code numbe*r `mandatory`
- page=*page number* `mandatory`(
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
### Updates

**Update 1.4 (March 2021)** :
Mihoyo has changed the pagination mechanic. They added an `id` for each wish and a parameter `en_id` in the url. To get the wishes in a page you need to provide the last wish id from the previous page in the `en_id` parameter. If you do not provide a valid `en_id` or `en_id` is missing the API will return the first page.

**Update February 2021** : 
`item_id` is no longer filled in response

---

### Get gatcha banners (JSON)

```jsx
https://hk4e-api-os.mihoyo.com/event/gacha_info/api/getConfigList?authkey_ver=1&sign_type=2&auth_appid=webview_gacha&init_type=301&gacha_id=eb44e687757162d2cd66b5c6bfaf980e5b7cf1&region=os_euro&lang=en&device_type=pc&ext=%7b%22loc%22%3a%7b%22x%22%3a1908.957763671875%2c%22y%22%3a200.475341796875%2c%22z%22%3a-1279.7091064453125%7d%7d&game_version=OSRELWin1.0.1_R1284249_S1393824_D1358691&authkey=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX&game_biz=hk4e_global
```

### Get banner items list (JSON)

```jsx
https://webstatic-sea.mihoyo.com/hk4e/gacha_info/os_euro/items/en-us.json
```

**Be careful Items are not always updated by miHoYo**
