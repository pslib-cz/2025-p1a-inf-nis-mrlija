<a id="home"></a>

# [PetRescue](https://pslib-cz.github.io/2025-p1a-inf-nis-mrlija)

<div align="center">
  <a href="https://pslib-cz.github.io/2025-p1a-inf-nis-mrlija">
    <img src="assets/banner.png" alt="Banner"/>
  </a>
</div>

## Použité umělé inteligence

<div align="center">
  <a href="https://chat.openai.com"><img src="https://custom-icon-badges.demolab.com/badge/ChatGPT-74aa9c?logo=openai&logoColor=white&style=for-the-badge" alt="ChatGPT" /></a>
  <a href="https://claude.ai"><img src="https://img.shields.io/badge/Claude-D97757?logo=claude&logoColor=fff&style=for-the-badge" alt="Claude" /></a>
  <a href="https://github.com/copilot"><img src="https://img.shields.io/badge/GitHub%20Copilot-000?logo=githubcopilot&logoColor=fff&style=for-the-badge" alt="GitHub Copilot" /></a>
  <a href="https://gemini.google.com"><img src="https://img.shields.io/badge/Google%20Gemini-886FBF?logo=googlegemini&logoColor=fff&style=for-the-badge" alt="Gemini" /></a>
</div>

## O projektu

PetRescue je moderní informační systém pro zvířecí útulky a záchranné stanice, který digitalizuje a zjednodušuje celý proces adopce.

### Téma

Digitalizace zvířecích útulků a modernizace adopčního procesu.

### Perex

Hledání nového domova pro opuštěná zvířata nebylo nikdy jednodušší. PetRescue je moderní informační systém, který efektivně propojuje záchranné stanice se zájemci o adopci. Zatímco veřejnosti nabízí přehledný online katalog mazlíčků s možností okamžitého podání žádosti, personálu útulku poskytuje silný nástroj pro evidenci svěřenců, správu zdravotních záznamů a rychlou administraci celého schvalovacího procesu. Cílem je minimum papírování a maximum zachráněných životů.

### Cílová skupina

Systém je určen především zaměstnancům a dobrovolníkům zvířecích útulků, záchranných stanic a dalších zařízení pečujících o opuštěná zvířata. Druhou skupinu tvoří veřejnost, tedy lidé, kteří si chtějí zvíře adoptovat, podívat se na jeho profil nebo podat žádost o adopci.

<p align="right">(<a href="#home">zpět na začátek</a>)</p>

## Použitelné technologie

<div align="center">
  <a href="https://nextjs.org"><img src="https://img.shields.io/badge/Next.js-000?logo=nextdotjs&logoColor=fff&style=for-the-badge" alt="Next.js" /></a>
  <a href="https://www.typescriptlang.org"><img src="https://img.shields.io/badge/TypeScript-3178c6?logo=typescript&logoColor=fff&style=for-the-badge" alt="TypeScript" /></a>
  <a href="https://tailwindcss.com"><img src="https://img.shields.io/badge/Tailwind%20CSS-06b6d4?logo=tailwindcss&logoColor=fff&style=for-the-badge" alt="Tailwind CSS" /></a>
  <a href="https://trpc.io"><img src="https://img.shields.io/badge/tRPC-398ccb?logo=trpc&logoColor=fff&style=for-the-badge" alt="tRPC" /></a>
  <a href="https://betterauth.dev"><img src="https://img.shields.io/badge/BetterAuth-0ea5a4?logo=auth0&logoColor=fff&style=for-the-badge" alt="BetterAuth" /></a>
  <a href="https://www.prisma.io"><img src="https://img.shields.io/badge/Prisma-2d3748?logo=prisma&logoColor=fff&style=for-the-badge" alt="Prisma" /></a>
  <a href="https://eslint.org"><img src="https://img.shields.io/badge/ESLint-4B32C3?logo=eslint&logoColor=fff&style=for-the-badge" alt="ESLint" /></a>
</div>

<p align="right">(<a href="#home">zpět na začátek</a>)</p>

## ER diagramy

Níže jsou dva návrhy ER diagramu pro systém PetRescue — přehledový diagram a detailní diagram s atributy.

### Přehledový ER diagram

```mermaid
erDiagram
    SHELTER ||--o{ PET : houses
    PET }o--|| SPECIES : is_of
    USER ||--o{ ADOPTION_REQUEST : submits
    PET ||--o{ ADOPTION_REQUEST : requested_for
    PET ||--o{ MEDICAL_RECORD : has
    PET ||--o{ PHOTO : has
    VOLUNTEER }o--|| SHELTER : works_at
    STAFF }o--|| SHELTER : employed_at
```

### Detailní ER diagram (atributy)

```mermaid
erDiagram
    SHELTER {
      uuid id PK
      string name
      string address
      string contact_email
    }

    PET {
      uuid id PK
      string name
      date birthdate
      string gender
      string status
      uuid shelter_id FK
      uuid species_id FK
    }

    SPECIES {
      uuid id PK
      string common_name
      string breed
    }

    USER {
      uuid id PK
      string full_name
      string email
      string phone
      string role
    }

    ADOPTION_REQUEST {
      uuid id PK
      uuid user_id FK
      uuid pet_id FK
      date requested_at
      string status
      text message
    }

    MEDICAL_RECORD {
      uuid id PK
      uuid pet_id FK
      date record_date
      string description
      boolean vaccinated
    }

    PHOTO {
      uuid id PK
      uuid pet_id FK
      string url
      string caption
    }

    VOLUNTEER {
      uuid id PK
      uuid user_id FK
      date start_date
    }

    STAFF {
      uuid id PK
      uuid user_id FK
      string position
    }

    %% Vztahy
    SHELTER ||--o{ PET : houses
    PET }o--|| SPECIES : is_of
    USER ||--o{ ADOPTION_REQUEST : submits
    PET ||--o{ ADOPTION_REQUEST : requested_for
    PET ||--o{ MEDICAL_RECORD : has
    PET ||--o{ PHOTO : has
    VOLUNTEER }o--|| SHELTER : works_at
    STAFF }o--|| SHELTER : employed_at
    VOLUNTEER ||--o{ PET : cares_for
```

Pokud chcete exporty do SVG/PNG nebo další rozšíření (např. separátní diagram pro workflow adopce), dejte vědět a doplním je.
