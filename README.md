# ADO.NET-connected-1---HuisGemaakt

<img src="images/1.jpg" height="400px">

Net zoals in de populaire Vlaamse show "Huis gemaakt", ga je de boel afbreken! In plaats van kamers te strippen, ga je in deze opgave ongewenste deelnemers verwijderen. Net zoals de deelnemers van de show hun badkamer vernieuwen, ga je UPDATE's uitvoeren om de gegevens in de rijen te verbeteren. Tot slot zal je geen nieuw huis bouwen, maar een nieuwe speler toevoegen: **JEZELF!**

Kortom jij krijgt de taak om gegevens te beheren van verschillende teams en spelers die meedoen aan deze bouwwedstrijd.

🏠 Veel succes! 🏠

## Aanmaken data
Gebruik de volgende scripts om je tabllen aan te maken in je database.

### Team tabel aanmaken
```
CREATE TABLE Team (
    ID INT PRIMARY KEY IDENTITY(1,1),
    Naam NVARCHAR(50) NOT NULL,
    Stad NVARCHAR(50) NOT NULL,
    Score INT DEFAULT 0
);

```


### Speler tabel aanmaken
```
CREATE TABLE Speler (
    ID INT PRIMARY KEY IDENTITY(1,1),
    Naam NVARCHAR(50) NOT NULL,
    Leeftijd INT NOT NULL,
    TeamID INT,
    FOREIGN KEY (TeamID) REFERENCES Team(ID) ON DELETE CASCADE
);

```

### Team tabel invullen

```
INSERT INTO Team (Naam, Stad, Score) VALUES 
('Team 1 Mechelen', 'Mechelen', 85),
('Team 2 Mechelen', 'Mechelen', 78),
('Team 1 Lummen', 'Lummen', 90),
('Team 2 Lummen', 'Lummen', 88),
('Team 1 Haasdonk', 'Haasdonk', 80),
('Team 2 Haasdonk', 'Haasdonk', 70),
('Team 1 Nieuwpoort', 'Nieuwpoort', 95),
('Team 2 Nieuwpoort', 'Nieuwpoort', 85);

```

### Speler tabel invullen

```
INSERT INTO Speler (Naam, Leeftijd, TeamID) VALUES
-- Mechelen
('Ruth', 32, 1),
('Ashley', 25, 1),
('Bowdy', 79, 2),
('Emiel', 64, 2),

-- Lummen
('Iman', 35, 3),
('Nico', 37, 3),
('Mo', 33, 4),
('Daisy', 30, 4),

-- Haasdonk
('Meaghan', 22, 5),
('Soumaya', 27, 5),
('Manu', 24, 6),
('Eros', 28, 6),

-- Nieuwpoort
('Axelle', 21, 7),
('Luca', 25, 7),
('Seppe', 22, 8),
('Sarvar', 28, 8);

```

## Beheren data
Maak gebruik van ADO.NET connected componenten om je SQL queries uit te voeren. Je moet geen SELECT uitvoeren in deze opgave. Met andere woorden je maakt hier nog **geen** gebruik van `SqlDataAdapter`. Normaalgezien maak je een `ClassLibrary` om je Data-gerelateerde methodes in te bouwen. Kies zelf of je hiervan gebruik wil maken voor deze opgave.

### 1. Strippen
Het tweede team van Nieuwpoort is gediskwalificeerd nadat ze een onstuimige ruzie hadden buiten de opnames. Verwijder ze uit de tabellen.

### 2. Renoveren
1. Het tweede team van Mechelen zijn per ongeluk geregistreerd als senioren. Bowdy is echter 29 jaar tijdens de opnames en Emiel is 24 jaar. Corrigeer hun leeftijd in de tabel.
2. Eros heeft zijn naam niet gestolen: hij is verliefd geworden op beide teamgenoten van Team 1 in Haasdonk. Hij heeft besloten om over te lopen van team en zijn ex-partner, Manu, in de steek te laten en haar alleen een huis te laten bouwen. Plaats Eros in zijn nieuw team bij Meaghan en Soumaya. 

### 3. Heropbouw
Plaats jezelf in een nieuw team in Hasselt. Geef jezelf een teamscore van 100.

