**API Wiadomości Plus**

```md
- base URL (Gdańsk): https://uonetplus-wiadomosciplus.edu.gdansk.pl/gdansk/api/
```

**Endpointy**

```md
GET OdebraneNowe

- Pobiera nowe odebrane wiadomości

GET WyslaneNowe

- Pobiera nowe wysłane wiadomości (nieużywane na stronie)

Request (Query String)

- idTopWiadomosc: int (0)

Response (JSON)

- nie wiem pusta lista
```

```md
GET LiczbyNieodczytanych

- Pobiera liczbę nieodebranych wiadomości

Response (JSON)

- nie wiem pusta lista
```

```md
GET OdebraneSkrzynka

- Pobiera odebrane wiadomości wybranego użytkownika

GET WyslaneSkrzynka

- Pobiera wysłane wiadomości wybranego użytkownika

GET UsunieteSkrzynka

- Pobiera usunięte wiadomości wybranego użytkownika

Request (Query String)

- globalKeySkrzynka: str ("a4408f53-e2e1-47b0-be8d-049160a3da11")
- idLastWiadomosc: int (0)
- pageSize: int (50)

Response (JSON)

- nie wiem pusta lista
```

```md
GET DdsArchive

- Ekran "Pobieranie plików"

Response (JSON)

- nie wiem pusta lista
```

```md
GET Odebrane

- Pobiera odebrane wiadomości

GET Wyslane

- Pobiera wysłane wiadomości

GET Usuniete

- Pobiera usunięte wiadomości

GET Kopie

- Pobiera kopie robocze

Request (Query String)

- idLastWiadomosc: int (0)
- pageSize: int (50)

Response (JSON)

- nie wiem pusta lista
```
