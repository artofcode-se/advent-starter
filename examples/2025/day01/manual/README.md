# 2025 dag 1 · hantverksexempel

Läs originaluppgiften hos [Advent of Code](https://adventofcode.com/2025/day/1). Den här katalogen innehåller lösningsidéer och är därför en spoiler. Inga AoC-indata eller uppgiftstexter har kopierats hit.

Detta är ett AI-assisterat undervisningsexempel, inte en tävlingsinlämning. Det visar ett tydligt, explicit angreppssätt för hantverksspåret; det är inte påstått handskrivet av en deltagare. Båda delarna stöds. Lösningen har lokala tester, men är inte verifierad med en deltagares privata input eller ett godkännande från AoC.

## Kör från repots rot

```sh
python3 -m unittest discover -s examples/2025/day01/manual/tests
python3 examples/2025/day01/manual/src/solve.py --part 1 < .private/inputs/2025-01.txt
docker build -f examples/2025/day01/manual/Dockerfile -t advent-example-manual .
docker run --rm -i advent-example-manual --part 2 < .private/inputs/2025-01.txt
```

Testerna skapar egna data och jämför med en oberoende simulering av varje klick. De täcker flera varv, start på noll, tomma rader och felaktiga kommandon. Algoritmen utför konstant arbete per rotation och behöver inte skapa en lista över alla klick.

## Bygg vidare

Förklara varför startläget inte är en ny passage av noll. Lägg till egna gränsfall och jämför de två implementationerna. Prova sedan samma idé i ett annat språk och mät skillnaden mellan kod, tester och körmiljö.

Exemplen ligger utanför `days/` så att de inte registreras som dina egna lösningar. Skriv din egen dagslösning där. Om du återanvänder kod, ange det tydligt och använd rätt spår.
