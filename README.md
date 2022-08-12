# API UONET+ Wiadomości Plus

Base URL (Gdańsk): `https://uonetplus-wiadomosciplus.edu.gdansk.pl/gdansk/api/`

Autoryzacja przez nagłówek `Cookie`

## Obiekty

```
WiadomośćMeta: {
    apiGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
    data: ISO 8601 ("2022-08-11T23:58:20.81+02:00"),
    hasZalaczniki: bool (false),
    id: int (21),
    korespondenci: str ("Wielu adresatów (0)"),
    nieprzeczytanePrzeczytanePrzez: ??? (null),
    przeczytana: bool (true),
    skrzynka: str ("Stanisław Jelnicki - U - (placówka)"),
    temat: str ("test"),
    uzytkownikRola: int (1),
    wazna: bool (false)
}
```

```
Wiadomość: {
    apiGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
    data: ISO 8601 ("2022-06-21T18:16:16.443+02:00"),
    id: int (1234567),
    nadawca: str ("Stanisław Jelnicki - U - (placówka)"),
    odbiorcy: [
        "Stanisław Jelnicki - U - (placówka)",
    ],
    odczytana: bool (false),
    temat: str ("test"),
    tresc: str ("<p>test</p>"),
    zalaczniki: ??? ([])
}
```

```
KopiaRobocza: {
    globalKey: str ("00000000-0000-0000-0000-000000000000"),
    watekGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
    temat: str ("test"),
    tresc: str ("<p>test</p>"),
    nadawcaSkrzynkaGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
    adresaci: [
        {
            skrzynkaGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
            nazwa: str ("Stanisław Jelnicki - U - (placówka)")
        }
    ],
    "zalaczniki": []
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

- `list[WiadomośćMeta]`

---

### GET `LiczbyNieodczytanych`

Pobiera liczbę nieodebranych wiadomości

#### Response (JSON)

200

- nie wiem pusta lista

---

### GET `OdebraneSkrzynka`

Pobiera odebrane wiadomości wybranego użytkownika

### GET `WyslaneSkrzynka`

Pobiera wysłane wiadomości wybranego użytkownika

### GET `UsunieteSkrzynka`

Pobiera usunięte wiadomości wybranego użytkownika

### GET `KopieSkrzynka`

Pobiera kopie robocze wybranego użytkownika

#### Request (Query String)

- `globalKeySkrzynka`: `str` (`"00000000-0000-0000-0000-000000000000"`)
- `idLastWiadomosc`: `int` (`0`)
- `pageSize`: `int` (`50`)

#### Response (JSON)

200

- `list[WiadomośćMeta]`

---

### GET `DdsArchive`

Ekran "Pobieranie plików"

#### Response (JSON)

200

- nie wiem pusta lista

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

- `list[WiadomośćMeta]`

---

### GET `Ustawienia`

Pobiera ustawienia wybranego użytkownika

#### Request (Query String)

- `globalKeySkrzynka`: `str` (`"00000000-0000-0000-0000-000000000000"`)

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

```
{
    globalKeySkrzynka: str ("00000000-0000-0000-0000-000000000000"),
    trybWysylaniaPowiadomien: int (1),
    stopka: str | null ("<p>test</p>")
}
```

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
    oneDriveClientId: str ("00000000-0000-0000-0000-000000000000"),
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

---

### GET `Stopka`

Pobiera aktualnie ustawione stopki użytkowników

#### Response (JSON)

200

```
[
    {
        skrzynkaGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
        tresc: str ("<p>test</p>")
    }
]
```

---

### POST `StatystykiLogowan`

Informuje serwer o nowej sesji?

#### Response

204

---

### GET `Skrzynki`

Pobiera listę użytkowników

#### Response (JSON)

200

```
[
    {
        globalKey: str ("00000000-0000-0000-0000-000000000000"),
        nazwa: str ("Stanisław Jelnicki - U - (placówka)"),
        typUzytkownika: int (3)
    }
]
```

---

### GET `Kopia`

Pobiera szczegóły kopii roboczej

#### Request (Query String)

- `globalKey`: `str` (`"00000000-0000-0000-0000-000000000000"`)

#### Response (JSON)

200

- `KopiaRobocza`

---

### GET `OdebraneSzczegolyArchiwum`

Pobiera szczegóły zarchiwizowanej odebranej wiadomości

#### Request (Query String)

- `idWiadomosc`: `int` (`1234567`)

#### Response (JSON)

200

- `Wiadomość`

---

### GET `GrupyAdresatow`

Pobiera grupy adresatów

#### Request (Query String)

- `skrzynkaGlobalKey`: `str` (`"00000000-0000-0000-0000-000000000000"`)

#### Response (JSON)

200

```
[
    {
        nazwa: str ("test"),
        globalKey: str ("00000000-0000-0000-0000-000000000000"),
        id: int (0)
    }
]
```

---

### POST `GrupyAdresatow`

Tworzy nową grupę adresatów

#### Request (JSON)

```

{
     "skrzynkaGlobalKey": "a4408f53-e2e1-47b0-be8d-049160a3da11",
     "nazwa": "test",
     "adresaciSkrzynkiGlobalKeys": [
        "d06a33e6-55af-4c4a-917e-ef5ad0b1d040"
    ]
}
```

---

### GET `GrupaAdresatow`

Pobiera listę adresatów w grupie

#### Request (Query String)

- `grupaAdresatowSkrzynkaGlobalKey`: `str`
  (`"00000000-0000-0000-0000-000000000000"`)

#### Response (JSON)

200

```
[
    {
        skrzynkaGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
        skrzynkaNazwa: str ("Stanisław Jelnicki - U - (placówka)"),
        typUzytkownika: int (1)
    }
]
```

---

### DELETE `GrupyAdresatow`

Usuwa grupę adresatów

#### Request (Query String)

- `grupaAdresatowGlobalKey`: `str` (`"00000000-0000-0000-0000-000000000000"`)

#### Response

204

---

### GET `Uczniowie`

Pobiera adresatów którzy są uczniami

### GET `Opiekunowie`

Pobiera adresatów którzy są opiekunami

### GET `Pracownicy`

Pobiera adresatów którzy są pracownikami

#### Request (Query String)

- `globalKeySkrzynka`: `str` (`"00000000-0000-0000-0000-000000000000"`)

#### Response (JSON)

200

```
[
    {
        metadata: {
            role: list[int] ([5]),
            dziennikiZajeciaInneIds: list[int] ([]),
            przedmiotyIds: list[int] ([1234]),
            oddzialyIds: list[int] ([123]),
            oddzialyPrzedszkolneIds: list[int] ([]),
            oddzialyWychowankowieIds: list[int] ([]),
            oddzialyWychowawcyIds: list[int] ([]),
            oddzialyPrzedszkolneWychowawcyIds: list[int] ([]),
            oddzialyWychowankowieWychowawcyIds: list[int] ([])
        },
        skrzynkaGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
        nazwa: str ("Stanisław Jelnicki - U - (placówka)")
    }
]
```

---

### GET `WiadomoscNowa`

#### Request (JSON)

```
{
	globalKey: str ("00000000-0000-0000-0000-000000000000"),
	watekGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
	nadawcaSkrzynkaGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
	adresaciSkrzynkiGlobalKeys: list[str] (["00000000-0000-0000-0000-000000000000"]),
	tytul: str ("test"),
	tresc: str ("<p>test</p>"),
	zalaczniki: ??? ([])
}
```

#### Response

- mam nadzieję, że
- 204 bez body lub
- 200 z body `Wiadomość`
