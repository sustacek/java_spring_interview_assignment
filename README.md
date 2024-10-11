# Zadání

Vaším úkolem je napsat jednoduchou aplikaci založenou na SpringBoot. Dodaný build script by měl umožnit jednoduché lokální spuštění aplikace a její otestování (např. příkazem `curl` či nějakým REST klientem). Použijte JDK 17 jako runtime. Gradle pro build skript, případně Maven.

Aplikace bude obsahovat REST Controller, který:

1. bude mapován na URI `/interests-of-users` (pouze GET)
2. převezme od uživatele parametr `interests`
   - může mít 1-N hodnot
   - parametr je povinný, aspoň jedna hodnota je povinná (neprázdná)
3. Controller bude načítat data (uživatele a jejich zájmy) z jednoduché REST služby, která vrací JSON.
    - pro jednoduchost jde o statický soubor dostupný na URL "https://raw.githubusercontent.com/sustacek/java_spring_interview_assignment/refs/heads/main/server/get-users.json"
4. JSON přetransformuje tak, že vrátí uživatele podle zájmů, kdy vybere jenom ty zájmy, které přišly v parametru `interests`
5. Pokud daný zájem není v JSON uveden u žádného uživatele, vrátí se 200, kdy seznam uživatelů daného zájmu bude prázdný

Příklad formátu odpovědi, kde byly poslány hodnoty `reading` a `programming`:

```json
{
  "reading": [
    {
      "user_id": "123456",
      "name": "John Doe"
    },
    {
      "user_id": "62234222123113",
      "name": "Jane Doe"
    }
  ],
  "programming": [
    {
      "user_id": "62234222123113",
      "name": "Jane Doe"
    }
  ]
}
```

Řešení doručte jako veřejnou repo na github.com a pošlete nám odkaz. Repository může být i na jiném serveru podporujícím git protokol.