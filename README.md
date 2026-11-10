# Advent med ART of Code

Skapa ett eget publikt repo med **Use this template → Create a new repository**. Mallen har workflow, båda spåren och instruktioner klara. Du behöver ingen inloggning på vår sajt och ingen API-nyckel till oss.

**Alla deltagare visas på sajten.** Att ansluta repot och bekräfta AoC-kontot innebär publik medverkan. Att bara gå med i AoC-listan registrerar dig inte här.

## Kom igång

1. Gå med i ART of Codes privata lista på [Advent of Code 2025](https://adventofcode.com/2025/leaderboard/private) med koden `1487429-4647410c`.
2. Fyll i `aoc_user_id`, `display_name` och `year` i `advent.json`. AoC-ID finns under AoC Settings. Använd 2025 för övning och 2026 för premiären, med ett separat repo per år.
3. Pusha till repots ordinarie gren. Öppna **Actions → Publicera Advent-lösningar**. Lägg engångskoden från körningens sammanfattning i ditt AoC-visningsnamn. Synken bekräftar den normalt inom 15 minuter, därefter kan koden tas bort. Den gäller i 48 timmar.
4. Skriv lösning, egna tester, Dockerfile och README under `days/01/manual/` eller `days/01/agent/`. Ange språk och delar i `solution.json`.
5. Lämna svaret på AoC och pusha koden. Workflowet registrerar versionen; servern väntar på godkännande för rätt år, dag och del innan den analyserar.
6. Fortsätt förbättra och pusha. Historiken sparar nya commits; samma commit ger inga dubbletter. Workflowet kan också startas manuellt via **Run workflow**.

För testmiljön kan en repository variable `ADVENT_API_URL` peka på test-API:ts `/api/v1/github/push`. Standard är produktion på `https://aoc.artofcode.se/api/v1/github/push`. GitHub Actions behöver `contents: read` och `id-token: write`, vilket redan är angivet i workflowet. Token skapas kortvarigt av GitHub; du ska inte skapa en egen nyckel.

## Hitta i repot

```text
agent/                    Ditt eget agentsystem och dess instruktioner
days/01/manual/           Din egen dagslösning
days/01/agent/            Agentens producerade dagslösning
shared/                   Din återanvändbara kod
days/01/agent/run.json     Valfri rapport över verktyg och modeller
runs/                     Dokumentation av rapportformatet
examples/2025/day01/      Två färdiga undervisningsexempel (spoilers)
.private/                 Dina privata indata och lokala loggar; aldrig Git
.github/workflows/        Pushflödet till ART of Codes API
```

Färdiga exempel ligger utanför `days/` och registreras inte som dina egna lösningar. Båda skapades med AI-stöd för undervisning. Hantverksexemplet visar arbetssättet; det är inte en deltagares handskrivna tävlingsinlämning.

## Körkontrakt för dina lösningar

Bygg från repots rot med en Dockerfile per dag och spår:

```sh
docker build -f days/01/manual/Dockerfile -t advent-day01 .
docker run --rm -i advent-day01 --part 1 < .private/inputs/01.txt
```

Programmet läser stdin, skriver svaret på stdout och diagnostik på stderr. Testa med egna små data. Vår server gör statisk analys och kör aldrig din kod.

## Gör det lätt att lära av dig

Beskriv installation och versioner, körkommandon, tester, kodens huvudidé och ett förbättringsförslag. För agenten: dela instruktioner, verktyg/modeller, hur den startas och hur man ändrar flödet. Länka till inspiration. Topplistan länkar till ditt repo så att andra kan förstå, prova och bygga vidare.

## Modeller och topplistor

Låt agenten skriva en valfri `run.json` intill dagslösningens `solution.json`. Se [rapportformatet](runs/README.md). Rapportera faktiskt modell-ID från anropets svar, inte bara verktygsnamnet. Modeller märks alltid som självrapporterade. Samma modell räknas en gång per säsong; nya versioner och språk finns kvar i utforskningshistoriken.

Kodrader jämförs per dag, del och spår. Inlämningstid ger inga poäng.

## Öppet och privat

- Publicera egen kod, tester med egna data, Dockerfiles och agentinstruktioner.
- Publicera aldrig AoC:s uppgiftstext, personliga inputfiler, sessionscookies, modellnycklar eller råa agentloggar.
- `.gitignore` och `.dockerignore` hjälper men tar inte bort filer som redan checkats in.
- Deltagandet är publikt: när du ansluter ditt repo och bekräftar AoC-kontot visas namn, repolänk, stjärnor och analyser på sajten.
- Redovisa modeller och mänskliga ingripanden ärligt. Okända mätvärden ska inte gissas.

[Onboarding och spelregler](https://aoc.artofcode.se/kom-igang/) · [Stöd Eric Wastl och Advent of Code](https://adventofcode.com/2026/support)
