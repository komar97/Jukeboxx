Jukeboxx - version avec base persistante

Probleme corrige:
- L'ancienne app utilisait stock.db comme fichier local.
- Sur Streamlit Cloud, les fichiers crees/modifies localement peuvent etre supprimes au redemarrage.
- Cette version garde SQLite en local pour les tests, mais utilise PostgreSQL/Supabase si DATABASE_URL est defini.

Installation recommandee avec Supabase:
1. Creer un projet Supabase.
2. Recuperer l'URL de connexion PostgreSQL, format SQLAlchemy:
   postgresql+psycopg2://USER:PASSWORD@HOST:5432/postgres
3. Dans Streamlit Cloud, ajouter dans Secrets:
   DATABASE_URL = "postgresql+psycopg2://USER:PASSWORD@HOST:5432/postgres"
4. Deployer l'app. Les tables articles et mouvements seront creees automatiquement.

Test local sans Supabase:
- streamlit run app.py
- L'app utilisera stock.db localement.

Notes:
- Ne pas mettre DATABASE_URL dans GitHub en dur.
- Le fichier stock.db reste utile seulement pour le developpement local.
