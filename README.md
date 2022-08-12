# API UONET+ Wiadomości Plus

Base URL (Gdańsk): `https://uonetplus-wiadomosciplus.edu.gdansk.pl/gdansk/api/`

Autoryzacja przez nagłówek `Cookie`

## Obiekty

### WiadomośćMeta

```
{
    apiGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
    data: ISO 8601 ("2022-08-11T23:58:20.81+02:00"),
    hasZalaczniki: bool (false),
    id: int (21),
    korespondenci: str ("Wielu adresatów (0)"),
    nieprzeczytanePrzeczytanePrzez: ??? | null (null),
    przeczytana: bool (true),
    skrzynka: str ("Stanisław Jelnicki - U - (placówka)"),
    temat: str ("test"),
    uzytkownikRola: int (1),
    wazna: bool (false)
}
```

### Wiadomość

```
{
    apiGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
    data: ISO 8601 ("2022-06-21T18:16:16.443+02:00"),
    id: int (1234567),
    nadawca: str ("Stanisław Jelnicki - U - (placówka)"),
    odbiorcy: list[str] (["Stanisław Jelnicki - U - (placówka)"]),
    odczytana: bool (false),
    temat: str ("test"),
    tresc: str ("<p>test</p>"),
    zalaczniki: [
        {
            url: str ("https://gpe-my.sharepoint.com/..."),
            nazwaPliku: str ("test.pdf")
        }
    ]
}
```

### NowaWiadomość

```
{
    globalKey: str ("00000000-0000-0000-0000-000000000000"),
    watekGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
    nadawcaSkrzynkaGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
    adresaciSkrzynkiGlobalKeys: list[str] (["00000000-0000-0000-0000-000000000000"]),
    tytul: str ("test"),
    tresc: str ("<p>test</p>"),
    zalaczniki: [
        {
            url: str ("https://gpe-my.sharepoint.com/..."),
            nazwaPliku: str ("test.pdf")
        }
    ]
}
```

### Odpowiedź

```
{
    data: ISO 8601 ("2022-08-12T13:24:07.807+02:00"),
    apiGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
    uzytkownikSkrzynkaGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
    nadawcaSkrzynkaGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
    nadawcaSkrzynkaNazwa: str "Stanisław Jelnicki - U - (placówka)",
    adresaci: [
        {
            skrzynkaGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
            nazwa: str "Stanisław Jelnicki - U - (placówka)"
        }
    ],
    temat: str ("test"),
    tresc: str ("<p>test</p>"),
    zalaczniki: [
        {
            url: str ("https://gpe-my.sharepoint.com/..."),
            nazwaPliku: str ("test.pdf")
        }
    ],
    id: int (47)
}
```

### OdpowiedźArchiwum

```
{
    data: ISO 8601 ("2022-06-20T12:24:32.943+02:00"),
    nadawca: str ("Stanisław Jelnicki - U - (placówka)"),
    odbiorcy: list[str] (["Stanisław Jelnicki - U - (placówka)"],
    temat: str ("test"),
    tresc: str ("<p>test</p>"),
    zalaczniki: [
        {
            url: str ("https://gpe-my.sharepoint.com/..."),
            nazwaPliku: str ("test.pdf")
        }
    ],
    id: int (1234567)
}
```

### KopiaRobocza

```
{
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
    zalaczniki: [
        {
            url: str ("https://gpe-my.sharepoint.com/..."),
            nazwaPliku: str ("test.pdf")
        }
    ]
}
```

## Endpointy

### Foldery wiadomości

#### GET `Odebrane`

Pobiera odebrane wiadomości

#### GET `Wyslane`

Pobiera wysłane wiadomości

#### GET `Usuniete`

Pobiera usunięte wiadomości

#### GET `OdebraneArchiwum`

Pobiera odebrane wiadomości w archiwum

#### GET `WyslaneArchiwum`

Pobiera wysłane wiadomości w archiwum

#### GET `UsunieteArchiwum`

Pobiera usunięte wiadomości w archiwum

#### GET `Kopie`

Pobiera kopie robocze

#### Request (Query String)

- `idLastWiadomosc`: `int` (`0`)
- `pageSize`: `int` (`50`)

#### Response (JSON)

200

`list[WiadomośćMeta]`

---

#### GET `Skrzynki`

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

#### GET `OdebraneSkrzynka`

Pobiera odebrane wiadomości wybranego użytkownika

#### GET `WyslaneSkrzynka`

Pobiera wysłane wiadomości wybranego użytkownika

#### GET `UsunieteSkrzynka`

Pobiera usunięte wiadomości wybranego użytkownika

#### GET `KopieSkrzynka`

Pobiera kopie robocze wybranego użytkownika

#### Request (Query String)

- `globalKeySkrzynka`: `str` (`"00000000-0000-0000-0000-000000000000"`)
- `idLastWiadomosc`: `int` (`0`)
- `pageSize`: `int` (`50`)

#### Response (JSON)

200

`list[WiadomośćMeta]`

---

#### GET `OdebraneNowe`

Pobiera nowe odebrane wiadomości

#### GET `WyslaneNowe`

Pobiera nowe wysłane wiadomości (nieużywane na stronie)

#### Request (Query String)

- `idTopWiadomosc`: `int` (`0`)

#### Response (JSON)

200

`list[WiadomośćMeta]`

---

#### GET `LiczbyNieodczytanych`

Pobiera liczbę nieodebranych wiadomości

#### Response (JSON)

200

- nie wiem pusta lista

---

#### GET `DdsArchive`

Ekran "Pobieranie plików"

#### Response (JSON)

200

- nie wiem pusta lista

---

### Czytanie wiadomości

#### GET `WiadomoscSzczegoly`

#### Request (Query String)

- `apiGlobalKey`: `str` (`"00000000-0000-0000-0000-000000000000"`)

#### Response (JSON)

200

`Wiadomość`

---

#### GET `OdebraneSzczegolyArchiwum`

Pobiera szczegóły odebranej wiadomości w archiwum

#### GET `WyslaneSzczegolyArchiwum`

Pobiera szczegóły wysłanej wiadomości w archiwum

#### GET `UsunieteSzczegolyArchiwum`

Pobiera szczegóły usuniętej wiadomości w archiwum

#### Request (Query String)

- `idWiadomosc`: `int` (`1234567`)

#### Response (JSON)

200

`Wiadomość`

---

### Wysyłanie wiadomości

#### GET `WiadomoscNowa`

#### Request (JSON)

`NowaWiadomość`

#### Response

204

---

### Odpowiadanie i przekazywanie wiadomości

#### GET `WiadomoscOdpowiedzPrzekaz`

#### Request (Query String)

- `apiGlobalKey`: `str` (`"00000000-0000-0000-0000-000000000000"`)

#### Response (JSON)

200

`Odpowiedź`

---

#### GET `WiadomoscArchiwumOdpowiedzPrzekaz`

#### Request (Query String)

- `idWiadomosc`: `int` (`1234567`)

#### Response (JSON)

200

`OdpowiedźArchiwum`

---

### Usuwanie i przywracanie wiadomości

#### POST `MoveTrash`

Usuwa wiadomość

Pierwsze użycie przenosi wiadomość z Odebranych do Usuniętych, następne usuwa
wiadomość na zawsze

#### POST `RestoreTrash`

Przywraca wiadomość

#### Request (JSON)

```
list[str] (["00000000-0000-0000-0000-000000000000"])
```

#### Response

204

---

#### POST `DeleteArchiwum`

Usuwa wiadomość w archiwum

Pierwsze użycie przenosi wiadomość z Odebranych do Usuniętych, następne usuwa
wiadomość na zawsze

#### POST `RestoreTrashArchiwum`

Przywraca wiadomość w archiwum

#### Request (JSON)

```
list[int] ([1234567])
```

#### Response

204

---

### Kopie robocze

#### GET `Kopia`

Pobiera kopię roboczą

#### Request (Query String)

- `globalKey`: `str` (`"00000000-0000-0000-0000-000000000000"`)

#### Response (JSON)

200

`KopiaRobocza`

---

#### POST `Kopia`

Zapisuje kopię roboczą

#### Request (JSON)

`NowaWiadomość`

#### Response

204

---

#### DELETE `Kopie`

Usuwa kopie robocze

#### Request (Query String)

- `globalKeys[]`: `list[str]` (`"1df26cc7-475f-4f70-9678-29d978d82c42"`)

#### Response

204

---

### Drukowanie raportów

#### POST `OdebraneWydruk`

Przygotowuje raport wybranych odebranych wiadomości

#### POST `WyslaneWydruk`

Przygotowuje raport wybranych wysłanych wiadomości

#### Request (JSON)

```
{
    esbPrintoutParams: {
        guid: str ("00000000-0000-0000-0000-000000000000"),
        friendlyName: str ("Wiadomości odebrane")
    },
    input: {
        globalKeys: list[str] (["00000000-0000-0000-0000-000000000000"])
    }
}
```

#### Response

204

---

### Ustawienia

#### GET `Ustawienia`

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

#### POST `Ustawienia`

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

### Adresaci

#### GET `Uczniowie`

Pobiera adresatów którzy są uczniami

#### GET `Opiekunowie`

Pobiera adresatów którzy są opiekunami

#### GET `Pracownicy`

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

#### GET `GrupaAdresatow`

Pobiera adresatów w grupie

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

#### GET `GrupyAdresatow`

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

#### POST `GrupyAdresatow`

Tworzy grupę adresatów

#### Request (JSON)

```
{
     skrzynkaGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
     nazwa: str ("test"),
     adresaciSkrzynkiGlobalKeys: list[str] (["00000000-0000-0000-0000-000000000000"]
}
```

---

#### DELETE `GrupyAdresatow`

Usuwa grupę adresatów

#### Request (Query String)

- `grupaAdresatowGlobalKey`: `str` (`"00000000-0000-0000-0000-000000000000"`)

#### Response

204

---

### Różne

#### GET `Cache`

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
            elementy: ??? | null (null),
            nazwa: str ("Uczeń"),
            link: str ("https://uonetplus-uczen.edu.gdansk.pl/gdansk/placowka/LoginEndpoint.aspx"),
            modul: int (0)
        }
    ],
    "wiadomoscPowitalnaOn": bool (false)
}
```

---

#### GET `Stopka`

Pobiera aktualnie ustawione stopki użytkowników

#### Response (JSON)

200

```
[
    {
        skrzynkaGlobalKey: str ("00000000-0000-0000-0000-000000000000"),
        tresc: str | null ("<p>test</p>")
    }
]
```

---

#### POST `StatystykiLogowan`

Informuje serwer o nowej sesji?

#### Response

204
