# Genshin Impact Wish History Web API (Global version)

---

### Get wish history (JSON)

```jsx
https://hk4e-api-os.hoyoverse.com/event/gacha_info/api/getGachaLog?authkey_ver=1&sign_type=2&auth_appid=webview_gacha&init_type=301&lang=en&authkey=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX&gacha_type=301&page=1&size=6&end_id=0
```

**Base URL** : https://hk4e-api-os.hoyoverse.com/event/gacha_info/api/getGachaLog
*Disclaimer : the base URL may differ on chinese version of the game*

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
    "data":
    {
        "page": "1",
        "size": "6",
        "total": "0",
        "list":
        [
            {
                "uid": "700000000",
                "gacha_type": "301",
                "item_id": "",
                "count": "1",
                "time": "2021-11-24 22:18:45",
                "name": "Albedo",
                "lang": "en-us",
                "item_type": "Character",
                "rank_type": "5",
                "id": "1637787960000243756"
            },
            {
                "uid": "700000000",
                "gacha_type": "301",
                "item_id": "",
                "count": "1",
                "time": "2021-11-24 22:18:45",
                "name": "Rosaria",
                "lang": "en-us",
                "item_type": "Character",
                "rank_type": "4",
                "id": "1637787960000243656"
            },
            {
                "uid": "700000000",
                "gacha_type": "301",
                "item_id": "",
                "count": "1",
                "time": "2021-11-24 22:18:45",
                "name": "Magic Guide",
                "lang": "en-us",
                "item_type": "Weapon",
                "rank_type": "3",
                "id": "1637787960000243556"
            },
            {
                "uid": "700000000",
                "gacha_type": "301",
                "item_id": "",
                "count": "1",
                "time": "2021-11-24 22:18:45",
                "name": "Ferrous Shadow",
                "lang": "en-us",
                "item_type": "Weapon",
                "rank_type": "3",
                "id": "1637787960000243456"
            },
            {
                "uid": "700000000",
                "gacha_type": "301",
                "item_id": "",
                "count": "1",
                "time": "2021-11-24 22:18:45",
                "name": "Magic Guide",
                "lang": "en-us",
                "item_type": "Weapon",
                "rank_type": "3",
                "id": "1637787960000243356"
            },
            {
                "uid": "700000000",
                "gacha_type": "400",
                "item_id": "",
                "count": "1",
                "time": "2021-11-24 22:18:28",
                "name": "Sharpshooter's Oath",
                "lang": "en-us",
                "item_type": "Weapon",
                "rank_type": "3",
                "id": "1637787960000237756"
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

### Update 2.5 (January 2022)
API domain changed from hk4e-api-os.mihoyo.com to hk4e-api-os.hoyoverse.com
