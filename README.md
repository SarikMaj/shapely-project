# Představení knihovny Shapely

Semestrální projekt. Repozitář obsahuje Jupyter Notebook, který v cca 20 minutách představuje knihovnu **[Shapely](https://shapely.readthedocs.io/)**, její využití i limity a demonstruje ji na reálných datech Natural Earth – většinu ukázek na České republice, některé na celém světě.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SarikMaj/shapely-project/blob/main/shapely_projekt.ipynb)

## O knihovně

Shapely je Python knihovna pro práci s rovinnou geometrií (body, linie, polygony). Je postavená nad C++ knihovnou GEOS, kterou používají i QGIS a PostGIS, a tvoří geometrický základ knihovny GeoPandas. Umí testovat prostorové vztahy (`contains`, `intersects`…) a provádět geometrické operace (`buffer`, `intersection`, `union`, `simplify`…). Neřeší čtení souborů, atributy ani souřadnicové systémy – na to se kombinuje s GeoPandas a pyproj.

## Obsah notebooku

Prezentace je postavená jako ukázka na reálných datech (většinou Česká republika). Každá funkce Shapely se představí ve chvíli, kdy ji analýza potřebuje:

1. **Data** – typy geometrie na skutečných objektech (ČR, Středočeský kraj s „dírou“ Praha, Vltava, Praha)
2. **Rozlohy krajů** – převod do S-JTSK, `area`, `length`, `union_all`, `symmetric_difference`
3. **Sousedé krajů** – predikáty `touches`, `within`
4. **Města a kraje** – vektorizovaný `contains`
5. **Vzdálenost od hranice** – `distance`, `nearest_points`, `buffer`, `difference`
6. **Řeky** – `intersection`, `intersects`, délky toků
7. **Města u řek** – pásmo 5 km (`buffer`)
8. **Spádové oblasti** – `voronoi_polygons`
9. **Popisky** – `centroid` vs. `representative_point` (Chorvatsko, kraje ČR)
10. **Celý svět** – prostorový index `STRtree`
11. **Zjednodušení hranice** – `simplify`
12. **Limity** – rovinné výpočty, nevalidní geometrie, přesnost čísel

## Použitá data

[Natural Earth](https://www.naturalearthdata.com/) v měřítku 1 : 10 mil. (public domain):

| Vrstva | Obsah |
|---|---|
| `ne_10m_admin_0_countries` | hranice států světa |
| `ne_10m_admin_1_states_provinces` | kraje ČR a regiony ostatních států |
| `ne_10m_populated_places_simple` | významná sídla světa |
| `ne_10m_rivers_lake_centerlines`, `ne_10m_rivers_europe` | řeky |

Data se při prvním spuštění notebooku **automaticky stáhnou** z [GitHub repozitáře Natural Earth](https://github.com/nvkelso/natural-earth-vector) do složky `data/`. Nic není potřeba stahovat ručně.

## Spuštění

**Google Colab:** klikněte na odznak *Open in Colab* výše a spusťte všechny buňky (*Runtime → Run all*).

**Lokálně:**

```bash
git clone https://github.com/SarikMaj/shapely-project.git
cd shapely-project
pip install -r requirements.txt
jupyter notebook shapely_projekt.ipynb
```

Notebook je otestovaný se Shapely 2.2, GeoPandas 1.2 a Pythonem 3.12. Vyžaduje Shapely **2.0 nebo novější** (vektorizované funkce, `shapely.plotting`, `voronoi_polygons`).

## Struktura repozitáře

```
├── shapely_projekt.ipynb   # hlavní notebook s výkladem a kódem
├── requirements.txt        # potřebné knihovny
├── README.md               # tato dokumentace
└── data/                   # vytvoří se automaticky po spuštění
```

## Zdroje

* Dokumentace Shapely – https://shapely.readthedocs.io/
* GEOS – https://libgeos.org/
* GeoPandas – https://geopandas.org/
* pyproj – https://pyproj4.github.io/pyproj/
* Natural Earth – https://www.naturalearthdata.com/
