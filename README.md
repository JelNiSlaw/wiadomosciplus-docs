# API UONET+ Wiadomości Plus

Base URL (Gdańsk): `https://uonetplus-wiadomosciplus.edu.gdansk.pl/gdansk/api/`

Autoryzacja przez nagłówek `Cookie`

## Obiekty

```
Wiadomość: {
    apiGlobalKey: str ("76512a0b-f2f5-4100-8f0b-f3876d53cd62"),
    data: ISO 8601 ("2022-08-11T23:58:20.81+02:00"),
    hasZalaczniki: bool (false),
    id: int (21),
    korespondenci: str ("Wielu adresatów (0)"),
    nieprzeczytanePrzeczytanePrzez: ??? (null),
    przeczytana: bool (true),
    skrzynka: str (Stanisław Jelnicki - U - (placówka)),
    temat: str ("test"),
    uzytkownikRola: int (1),
    wazna: bool (false)
}
```

## Endpointy

### GET `OdebraneNowe`

Pobiera nowe odebrane wiadomości

### GET `WyslaneNowe`

Pobiera nowe wysłane wiadomości (nieużywane na stronie)

#### Request (Query String)

- `idTopWiadomosc`: `int` (`0`)

#### Response (JSON)

200

- `list[Wiadomość]`

---

### GET `LiczbyNieodczytanych`

Pobiera liczbę nieodebranych wiadomości

#### Response (JSON)

200

- `list[Wiadomość]`

---

### GET `OdebraneSkrzynka`

Pobiera odebrane wiadomości wybranego użytkownika

### GET `WyslaneSkrzynka`

Pobiera wysłane wiadomości wybranego użytkownika

### GET `UsunieteSkrzynka`

Pobiera usunięte wiadomości wybranego użytkownika

#### Request (Query String)

- `globalKeySkrzynka`: `str` (`"a4408f53-e2e1-47b0-be8d-049160a3da11"`)
- `idLastWiadomosc`: `int` (`0`)
- `pageSize`: `int` (`50`)

#### Response (JSON)

200

- `list[Wiadomość]`

---

### GET `DdsArchive`

Ekran "Pobieranie plików"

#### Response (JSON)

200

- `list[Wiadomość]`

---

### GET `Odebrane`

Pobiera odebrane wiadomości

### GET `Wyslane`

Pobiera wysłane wiadomości

### GET `Usuniete`

Pobiera usunięte wiadomości

### GET `Kopie`

Pobiera kopie robocze

### GET `OdebraneArchiwum`

Pobiera zarchiwizowane odebrane wiadomości

### GET `WyslaneArchiwum`

Pobiera zarchiwizowane wysłane wiadomości

### GET `UsunieteArchiwum`

Pobiera zarchiwizowane usunięte wiadomości

#### Request (Query String)

- `idLastWiadomosc`: `int` (`0`)
- `pageSize`: `int` (`50`)

#### Response (JSON)

200

- `list[Wiadomość]`

---

### GET `Ustawienia`

Pobiera ustawienia wybranego użytkownika

#### Request (Query String)

- `globalKeySkrzynka`: `str` (`"a4408f53-e2e1-47b0-be8d-049160a3da11"`)

#### Response (JSON)

200

```
{
    stopka: str | null ("<p>test</p>"),
    trybWysylaniaPowiadomien: int (1)
}
```

---

### POST `Ustawienia`

Modyfikuje ustawienia wybranego użytkownika

#### Request (JSON)

- `globalKeySkrzynka`: `str` (`"a4408f53-e2e1-47b0-be8d-049160a3da11"`)
- `stopka`: `str | null` (`"<p>test</p>"`)
- `trybWysylaniaPowiadomien`: `int` (`1`)

#### Response

204

---

### GET `Cache`

Pobiera drobne ustawienia

#### Response (JSON)

200

```
{
    googleDriveApiKey: str (""),
    googleDriveClientId: str (""),
    oneDriveClientId: str ("ca12431d-6b51-4489-ad8d-166b0cda986c"),
    links: [
        {
            elementy: ??? (null),
            nazwa: str ("Uczeń"),
            link: str ("https://uonetplus-uczen.edu.gdansk.pl/gdansk/placowka/LoginEndpoint.aspx"),
            modul: int (0)
        }
    ],
    "wiadomoscPowitalnaOn": bool (false)
}
```
