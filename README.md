# AnimePahe Scraper API 

## Features

- Search anime by query
- Get all episodes for a given anime session
- Retrieve source links for a specific episode
- Resolve `.m3u8` URLs from Kwik or embedded players
- FastAPI backend for easy integration with frontends or other tools
- Async, efficient, and capable of bypassing Cloudflare restrictions

---
## 📡 API Endpoints

Once deployed, your API will have these endpoints:

- `GET /` - API information
- `GET /health` - Health check
- `GET /search?q=naruto` - Search anime
- `GET /episodes?session=<session>` - Get episodes
- `GET /sources?anime_session=<session>&episode_session=<session>` - Get sources
- `GET /m3u8?url=<kwik-url>` - Resolve M3U8 URL
- `GET /player.html` - Video player demo



## 📝 Environment Variables

No environment variables needed! The app works out of the box.


**Note:** M3U8 resolution takes 2-3 seconds, well within the timeout.

## Example JSON

```http
GET /search?q=naruto
```

Output:

```json
[
  {
    "id": 1571,
    "title": "Naruto",
    "url": "https://animepahe.com/anime/77bbe16e-fd87-13d9-a18c-4edb06884a33",
    "year": 2002,
    "poster": "https://i.animepahe.com/posters/85d36625d8fe4e51d4deb9ea4a543d71ed6397b5c439d4fc6dd0bc62861e03d2.jpg",
    "type": "TV",
    "session": "77bbe16e-fd87-13d9-a18c-4edb06884a33"
  },
  {
    "id": 1,
    "title": "Naruto Shippuden",
    "url": "https://animepahe.com/anime/623e7c17-bfe4-d666-58eb-a6a934012011",
    "year": 2007,
    "poster": "https://i.animepahe.com/posters/f4c50c796beaddb3cb27f88bea181ce858768de4e6c59e37519fc15870472db8.jpg",
    "type": "TV",
    "session": "623e7c17-bfe4-d666-58eb-a6a934012011"
  },
  {
    "id": 1012,
    "title": "Naruto Spin-Off: Rock Lee & His Ninja Pals",
    "url": "https://animepahe.com/anime/4bdd6e0c-ac0c-3908-9587-874b4bf29117",
    "year": 2012,
    "poster": "https://i.animepahe.com/posters/5d01b49ef31cdc6f5a4ba1e220244d3fb5e2fe4c122473c06f453da21c1ec1fa.jpg",
    "type": "TV",
    "session": "4bdd6e0c-ac0c-3908-9587-874b4bf29117"
  }
]
```

---

```http
GET /episodes?session=27a95751-0311-47ed-dbce-7f0680d5074a
```

Output:

```json
[
  {
    "id": 70730,
    "number": 1,
    "title": "Episode 1",
    "snapshot": "https://i.animepahe.si/uploads/snapshots/22c034f704a286b5ce17cc33a3dccf9258cc83038e5bafbcc5a196b2584c3454.jpg",
    "session": "800a1f7d29d6ebb94d2bfd320b2001b95d00decff4aaecaa6fbef5916379a762"
  },
  {
    "id": 70823,
    "number": 2,
    "title": "Episode 2",
    "snapshot": "https://i.animepahe.si/uploads/snapshots/baf28a9ea1fecf9bbee49844cf3b782632e487ff49d3ba5c93b56241719fab05.jpg",
    "session": "4dd535ded2d2773bb3285881839d018c5787619de262dffb801ab4f78cf20123"
  }
]
```

---

```http
GET /sources?anime_session=27a95751-0311-47ed-dbce-7f0680d5074a&episode_session=800a1f7d29d6ebb94d2bfd320b2001b95d00decff4aaecaa6fbef5916379a762
```

Output:

```json
[
  {
    "url": "https://kwik.si/e/KcfYGhr86Ww2",
    "quality": "1080p",
    "fansub": "KawaSubs",
    "audio": "jpn"
  },
  {
    "url": "https://kwik.si/e/Sr2gRRoVz6wy",
    "quality": "720p",
    "fansub": "KawaSubs",
    "audio": "jpn"
  },
  {
    "url": "https://kwik.si/e/J7jBHBSJhTEv",
    "quality": "360p",
    "fansub": "KawaSubs",
    "audio": "jpn"
  }
]
```

---

```http
GET /m3u8?url=https://kwik.si/e/uEPQKLMzFpaz
```

Output:

```json
{
  "m3u8": "https://vault-12.owocdn.top/stream/12/12/1478df0e98f767de547ac36d33bc92b73b9a5b7318fe3f3e81328fa31fc1eac3/uwu.m3u8"
}
```



