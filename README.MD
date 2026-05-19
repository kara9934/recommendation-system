


LES Tables

utilisateurs
formation
bourse
recommandations

Creation des tables
----- la table utilisateurs -------------
CREATE TABLE utilisateurs(
    id SERIAL PRIMARY KEY,
    nom VARCHAR(100) NOT NULL,
    prenom VARCHAR(100) NOT NULL,
    email VARCHAR(200) UNIQUE NOT NULL,
    age INTEGER,
    pays VARCHAR(100) NOT NULL,
    niveau_etude VARCHAR(50) NOT NULL,
    domaine VARCHAR(100) NOT NULL,
    objectif VARCHAR(100),
    langue VARCHAR(50) DEFAULT 'francais',
    created_at TIMESTAMP DEFAULT NOW()
);

----- la table formation (((((((())))))))
CREATE TABLE formations(
    id SERIAL PRIMARY KEY,
    titre VARCHAR(300) NOT NULL,
    descriptions TEXT,
    domaine VARCHAR(100) NOT NULL,
    niveau_requis VARCHAR(50) NOT NULL,
    pays_disponible VARCHAR(100) DEFAULT 'international',
    langue VARCHAR(50) DEFAULT 'francais',
    duree VARCHAR(100),
    est_gratuit BOOLEAN DEFAULT FALSE,
    lien VARCHAR(500),
    organisme VARCHAR(200),
    created_at TIMESTAMP DEFAULT NOW()
);

------ la table bourse -----------------
CREATE TABLE bourses(
    id SERIAL PRIMARY KEY,
    titre VARCHAR(300) NOT NULL,
    descriptions TEXT,
    organisme VARCHAR(200) NOT NULL,
    domaine VARCHAR(100) NOT NULL,
    pays_eligible VARCHAR(100) DEFAULT 'tous',
    niveau_requis VARCHAR(50) NOT NULL,
    montant VARCHAR(200),
    date_limite DATE,
    type_bourse VARCHAR(100),
    lien VARCHAR(500)
    created_at TIMESTAMP DEFAULT NOW()
);

------------ la table recommandations ------------
CREATE TABLE recommandations(
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES utilisateurs(id) ON DELETE CASCADE,
    item_id INTEGER NOT NULL,
    type_item VARCHAR(20) NOT NULL,
    score INTEGER NOT NULL,
    raisons TEXT,
    created_at TIMESTAMP DEFAULT NOW()
    );


<!-- Insertion des données dans les tables -->

--- la table formation ------
INSERT INTO formations
    (titre, description, domaine, niveau_requis, pays_disponible, langue, dureee, est_gratuit, lien, organisme
    )

VALUES
-- formation 1
('introduction à python et Data Science,
'apprenez les bases de python et de l'analyse de donnees avec des projets concrets. Idéal pour debuter en Data Science',
'Informatique', 'lycees', 'international', 'francais', '8 semaines', TRUE,
' https://www.coursera.org', 'Coursera \ IBM'
)

--- la table bourses ---------------
INSERT INTO bourses
(
    titre, descriptions, organisme, pays_eligible, niveau_requis, domaine, montant, type_bourse, lien
)

VALUES
(
    'Bourse Excellence AFD_Master en France',
    'Financement complet pour etudier en France. Couvre frais de scolarite, billet avion et vie.',
    'Agence Francaise de developpement',
    'tous',
    'licence', 
    'informatique',
    'Frais de scolarite + 850 euro/mois',
    'excellence',
    'https://www.afd.fr'
    '
),

### la table utilisateurs ---------------

INSERT INTO utilisateurs (nom, prenom, email, age, pays, niveau_etude, domaine, objectif)
VALUES
('Kouassi', 'Jean', 'jean.kouassi@gmail.com', 25, 'Côte d''Ivoire', 'Licence', 'Informatique', 'Etudier à l''étranger'),
('Diallo', 'Aminata', 'aminata.diallo@gmail.com', 28, 'Sénégal', 'Master', 'Finance', 'Trouver une bourse'),
('Mensah', 'Kwame', 'kwame.mensah@gmail.com', 30, 'Ghana', 'Licence', 'Data Science', 'Se spécialiser'),
('Okoro', 'Chinedu', 'chinedu.okoro@gmail.com', 27, 'Nigeria', 'Master', 'Ingénierie', 'Doctorat'),
('Traoré', 'Fatou', 'fatou.traore@gmail.com', 24, 'Mali', 'Licence', 'Marketing', 'Formation professionnelle'),
('Nguessan', 'Paul', 'paul.nguessan@gmail.com', 26, 'Côte d''Ivoire', 'Master', 'Economie', 'Recherche'),
('Sarr', 'Moussa', 'moussa.sarr@gmail.com', 29, 'Sénégal', 'Licence', 'Gestion', 'Entrepreneuriat'),
('Koffi', 'Marie', 'marie.koffi@gmail.com', 23, 'Côte d''Ivoire', 'Licence', 'Droit', 'Etudier'),
('Toure', 'Ibrahim', 'ibrahim.toure@gmail.com', 31, 'Guinée', 'Master', 'IA', 'Recherche'),
('Banda', 'Grace', 'grace.banda@gmail.com', 27, 'Zambie', 'Licence', 'Santé', 'Spécialisation');


### la table formations ---------------

INSERT INTO formations (titre, descriptions, domaine, niveau_requis, pays_disponible, langue, duree, est_gratuit, lien, organisme)
VALUES
('Data Science Bootcamp', 'Formation intensive en data science', 'Data Science', 'Licence', 'International', 'Anglais', '6 mois', true, 'http://example.com', 'Coursera'),
('MBA Finance', 'Programme en finance', 'Finance', 'Master', 'USA', 'Anglais', '2 ans', false, 'http://example.com', 'Harvard'),
('Marketing Digital', 'Formation marketing', 'Marketing', 'Licence', 'France', 'Français', '3 mois', true, 'http://example.com', 'OpenClassrooms'),
('IA Avancée', 'Intelligence artificielle', 'IA', 'Master', 'Canada', 'Anglais', '1 an', false, 'http://example.com', 'Udemy'),
('Droit International', 'Droit global', 'Droit', 'Licence', 'France', 'Français', '1 an', false, 'http://example.com', 'Sorbonne'),
('Gestion de Projet', 'Project management', 'Gestion', 'Licence', 'International', 'Français', '4 mois', true, 'http://example.com', 'LinkedIn Learning'),
('Cybersécurité', 'Sécurité informatique', 'Informatique', 'Master', 'Allemagne', 'Anglais', '1 an', false, 'http://example.com', 'Udacity'),
('Analyse Economique', 'Macroéconomie', 'Economie', 'Licence', 'Belgique', 'Français', '6 mois', true, 'http://example.com', 'FUN MOOC'),
('Santé Publique', 'Santé globale', 'Santé', 'Licence', 'UK', 'Anglais', '1 an', false, 'http://example.com', 'WHO Academy'),
('Entrepreneuriat', 'Créer son entreprise', 'Business', 'Licence', 'International', 'Français', '3 mois', true, 'http://example.com', 'Google');

### la table bourses ---------------

INSERT INTO bourses (titre, descriptions, organisme, domaine, pays_eligible, niveau_requis, montant, date_limite, type_bourse, lien)
VALUES
('Bourse Eiffel', 'Etudes en France', 'Gouvernement Français', 'Tous', 'Afrique', 'Master', '1500€/mois', '2026-06-01', 'Partielle', 'http://example.com'),
('Bourse Fulbright', 'Etudes USA', 'USA Gov', 'Tous', 'International', 'Master', '2000$/mois', '2026-05-15', 'Complète', 'http://example.com'),
('Bourse Chevening', 'UK scholarship', 'UK Gov', 'Tous', 'Afrique', 'Master', 'Complet', '2026-07-01', 'Complète', 'http://example.com'),
('Bourse DAAD', 'Allemagne', 'DAAD', 'Ingénierie', 'Afrique', 'Master', '1000€/mois', '2026-06-10', 'Complète', 'http://example.com'),
('Bourse Canada', 'Etudes Canada', 'Canada Gov', 'Tous', 'International', 'Master', '1200$/mois', '2026-08-01', 'Partielle', 'http://example.com'),
('Bourse BAD', 'Banque Africaine', 'BAD', 'Finance', 'Afrique', 'Licence', '800$/mois', '2026-04-30', 'Partielle', 'http://example.com'),
('Bourse ONU', 'Programme ONU', 'ONU', 'Développement', 'International', 'Master', '1500$/mois', '2026-09-01', 'Complète', 'http://example.com'),
('Bourse Chine', 'Etudes Chine', 'Gov Chine', 'Tous', 'Afrique', 'Licence', 'Gratuit', '2026-06-20', 'Complète', 'http://example.com'),
('Bourse Inde', 'Etudes Inde', 'Gov Inde', 'IT', 'Afrique', 'Licence', '500$/mois', '2026-07-15', 'Partielle', 'http://example.com'),
('Bourse Japon', 'Etudes Japon', 'MEXT', 'Tous', 'International', 'Master', '1400$/mois', '2026-05-30', 'Complète', 'http://example.com');

### la table recommandations ---------------

INSERT INTO recommandations (user_id, item_id, type_item, score, raisons)
VALUES
(1, 1, 'formation', 90, 'Correspond au profil data'),
(2, 2, 'bourse', 85, 'Bonne adéquation finance'),
(3, 1, 'formation', 88, 'Data science adaptée'),
(4, 4, 'formation', 92, 'IA avancée pertinente'),
(5, 3, 'formation', 80, 'Marketing cohérent'),
(6, 8, 'formation', 87, 'Economie adaptée'),
(7, 10, 'formation', 83, 'Entrepreneuriat recommandé'),
(8, 5, 'formation', 78, 'Droit cohérent'),
(9, 4, 'bourse', 91, 'Bonne opportunité IA'),
(10, 9, 'formation', 86, 'Santé publique adaptée');


-----------------------------------------------------
-----------------------------------------------------
def bourse_en_texte(bourse):
    titre = bourse.get('titre', '')
    description = bourse.get('descriptions', '')
    organisme = bourse.get('organisme', '')
    domaine = bourse.get('domaine', '')
    pays = bourse.get('pays_eligible', '')
    montant = bourse.get('montant', '')
    date_limite = bourse.get('date_limite', '')
    type_bourse = bourse.get('type_bourse', '')
    lien = bourse.get('lien', '')

    texte = (
        f"Bourse '{titre}' en {domaine}, "
        f"destinée aux étudiants niveau {niveau}, "
        f"disponible pour : {pays}. "
        f"Type : {type_bourse}, montant : {montant}. "
        f"Proposée par {organisme}. "
        f"Date limite : {date_limite}. "
        f"Détails : {description}. "
        f"Lien : {lien}"
    )

    return texte