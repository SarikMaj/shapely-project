# Představení knihovny Shapely

Semestrální projekt do předmětu *Prostorová data v Pythonu*. Repozitář obsahuje Jupyter Notebook, který v cca 20 minutách představuje knihovnu **[Shapely](https://shapely.readthedocs.io/)**, její využití i limity a demonstruje ji na reálných prostorových datech České republiky.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SarikMaj/shapely-project/blob/main/shapely_projekt.ipynb)

## O knihovně

Shapely je Python knihovna pro práci s rovinnou geometrií (body, linie, polygony). Je postavená nad C++ knihovnou GEOS, kterou používají i QGIS a PostGIS, a tvoří geometrický základ knihovny GeoPandas. Umí testovat prostorové vztahy (`contains`, `intersects`…) a provádět geometrické operace (`buffer`, `intersection`, `union`, `simplify`…). Neřeší čtení souborů, atributy ani souřadnicové systémy – na to se kombinuje s GeoPandas a pyproj.

## Obsah notebooku

1. Co je Shapely a kam patří v ekosystému prostorových knihoven
2. Geometrické objekty (`Point`, `LineString`, `Polygon`, WKT, atributy)
3. Prostorové predikáty (DE-9IM)
4. Geometrické operace (buffer, průnik, sjednocení, rozdíl, konvexní obal, centroid vs. reprezentativní bod)
5. Praktická ukázka na datech ČR:
   * převod do S-JTSK (EPSG:5514) a výpočet rozlohy a délky hranic,
   * výběr měst ležících v ČR – srovnání cyklu a vektorizované funkce,
   * vzdálenost měst od státní hranice a nejbližší body,
   * ořez řek hranicí státu, délky toků, 5km pásmo kolem řek,
   * Voroného polygony („spádové oblasti“ měst),
   * prostorový index `STRtree` – celosvětové prostorové spojení sídel se státy,
   * zjednodušení hranice algoritmem Douglas–Peucker.
6. Limity: chybějící CRS a rovinné výpočty, nevalidní geometrie, přesnost `float`, pouze 2D, výkon
7. Alternativy, shrnutí a zdroje

## Použitá data

[Natural Earth](https://www.naturalearthdata.com/) v měřítku 1 : 10 mil. (public domain):

| Vrstva | Obsah |
|---|---|
| `ne_10m_admin_0_countries` | hranice států světa |
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
