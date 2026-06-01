# Katalog požadavků — PetRescue (NIS)

Datum: 2026-05-21

## 1. Úvod a účel

Tento dokument popisuje funkční a nefunkční požadavky pro informační systém PetRescue — systém pro evidenci zvířat v útulcích, správu adopcí, zdravotních záznamů a komunikaci se žadateli.

## 2. Rozsah systému

PetRescue umožní: registraci útulků a uživatelů, správu profilů zvířat (fotky, zdravotní záznamy), přijímání a zpracování žádostí o adopci, správu rolí (staff, volunteer, public) a auditní záznamy operací.

## 3. Slovníček

- Útulek: organizační jednotka držící zvířata (SHELTER).
- Zvíře: entita evidovaná v systému (PET).
- Žadatel: registrovaný uživatel, který může podávat žádosti o adopci (USER).
- Žádost o adopci: formulář odeslaný žadatelem pro konkrétní zvíře (ADOPTION_REQUEST).

## 4. Role (aktéři)

- Veřejnost / žadatel (Guest)
- Registrovaný uživatel
- Dobrovolník (Volunteer)
- Zaměstnanec útulku / pracovník (Staff)
- Administrátor systému (Admin)

## 5. Funkční požadavky (FR)

- FR-01: Registrovat a ověřit uživatele — systém umožní registraci uživatelů s ověřením emailu.
- FR-02: Přihlášení / autorizace — role-based přístup (public, volunteer, staff, admin).
- FR-03: CRUD útulků — administrátor může vytvářet a upravovat záznamy útulků.
- FR-04: CRUD zvířat — staff/volunteer může přidávat, upravovat nebo archivovat profily zvířat (jméno, věk, pohlaví, plemeno, status, umístění).
- FR-05: Fotogalerie zvířat — nahrávání a prohlížení fotografií pro každý profil zvířete.
- FR-06: Evidence zdravotních záznamů — staff může přidávat záznamy (očkování, ošetření, diagnozy).
- FR-07: Vyhledávání a filtrování zvířat — veřejnost může vyhledávat podle druhu, věku, lokality a stavu k adopci.
- FR-08: Podání žádosti o adopci — registrovaný uživatel může podat žádost pro konkrétní zvíře s doprovodným textem a kontaktními údaji.
- FR-09: Workflow zpracování žádosti — staff může žádosti prohlížet, měnit stav (nová, posouzena, schválena, zamítnuta) a přiřazovat schůzky.
- FR-10: Notifikace — systém odesílá emaily při důležitých změnách (potvrzení registrace, stav žádosti, upomínky).
- FR-11: Role a oprávnění — administrátor může přiřazovat role a práva uživatelům.
- FR-12: Audit a logování — systém zaznamenává změny klíčových entit (kdo a kdy upravil profil zvířete, žádost apod.).
- FR-13: Export dat — staff může exportovat seznamy zvířat a žádostí ve formátu CSV pro administrativní účely.

## 6. Nefunkční požadavky (NFR)

- NFR-01: Bezpečnost — komunikace přes HTTPS, uložení hesel bezpečným hashováním (bcrypt/argon2).
- NFR-02: Dostupnost — základní SLA cílově 99% dostupnost během provozních hodin.
- NFR-03: Škálovatelnost — návrh tak, aby bylo možné horizontální škálování frontendu a backendu.
- NFR-04: Výkon — stránky s katalogem zvířat se načtou do 3 sekund při běžné zátěži.
- NFR-05: Ochrana osobních údajů — shoda s GDPR (úprava a mazání osobních údajů po požadavku).
- NFR-06: Zálohování — pravidelné zálohy databáze (denní snapshoty) a obnova do 24 hodin.
- NFR-07: Přístupnost — základní WCAG kompatibilita pro veřejné stránky.

## 7. Systémové požadavky a omezení

- Databáze: relační DB (Postgres doporučeno) s ORM (Prisma).
- Autentizace: OAuth2 / session-based auth jako volitelná rozšíření.
- Integrace: e-mail provider (SMTP / SendGrid) pro notifikace.

## 8. Prioritizace

- Must: FR-01, FR-02, FR-04, FR-07, FR-08, FR-09, NFR-01, NFR-05
- Should: FR-05, FR-06, FR-10, FR-12, NFR-04
- Could: FR-03, FR-11, FR-13, NFR-02, NFR-06

## 9. Případy užití (stručně)

- UC-01: Žadatel vyhledá zvíře a podá žádost o adopci.
- UC-02: Staff přidá nové zvíře, vloží fotografie a zdravotní záznam.
- UC-03: Staff zpracuje žádost a oznámí žadateli výsledek.

## 10. Kritéria akceptace

- Hlavní katalog zvířat a detail zvířete jsou dostupné a prohledatelné.
- Registrovaný uživatel může podat žádost a staff ji vidí v administračním rozhraní.
- Záznamy o zdravotním stavu lze přidávat a zobrazovat.

## 11. Další kroky

- Vytvořit detailní wireframy administrace a veřejného katalogu.
- Vygenerovat UML sekvenční diagram workflow adopce.
- Naplánovat implementační sprinty podle priorit.

Při požadavku mohu tento katalog rozšířit o detailní acceptance tests a datové rozhraní API (endpoints).
