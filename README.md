# Představení knihovny Shapely

Semestrální projekt. Repozitář obsahuje Jupyter Notebook, který v cca 20 minutách představuje knihovnu **[Shapely](https://shapely.readthedocs.io/)** a demonstruje její využití na reálných datech Natural Earth – většinu ukázek na České republice, některé na celém světě.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SarikMaj/shapely-project/blob/main/shapely_projekt.ipynb)

## O knihovně

Shapely je Python knihovna pro práci s rovinnou geometrií (body, linie, polygony). Je postavená nad C++ knihovnou GEOS, kterou používají i QGIS a PostGIS, a tvoří geometrický základ knihovny GeoPandas. Umí testovat prostorové vztahy (`contains`, `intersects`…) a provádět geometrické operace (`buffer`, `intersection`, `union`, `simplify`…).

## Obsah notebooku

1. **Data** – načtení dat, výběr ČR a převod do metrů (S-JTSK)
2. **Typy geometrie** – polygon (ČR), linie (Vltava), bod (Praha)
3. **Rozlohy krajů** – `area`, `length`
4. **Sousedé krajů** – `touches`
5. **Města a kraje** – `contains`
6. **Vzdálenost od hranice** – `distance`, `nearest_points`
7. **Řeky a města u řek** – `intersection`, `buffer`, `union_all`
8. **Popisky** – `centroid` vs. `representative_point` (Chorvatsko)
9. **Celý svět** – prostorový index `STRtree`
10. **Zjednodušení hranice** – `simplify`

## Použitá data

[Natural Earth](https://www.naturalearthdata.com/) v měřítku 1 : 10 mil. (public domain):

| Vrstva | Obsah |
|---|---|
| `ne_10m_admin_0_countries` | hranice států světa |
| `ne_10m_admin_1_states_provinces` | kraje ČR a regiony ostatních států |
| `ne_10m_populated_places_simple` | významná sídla světa |
| `ne_10m_rivers_lake_centerlines`, `ne_10m_rivers_europe` | řeky |

Notebook data **načítá přímo z internetu** z [GitHub repozitáře Natural Earth](https://github.com/nvkelso/natural-earth-vector). Nic není potřeba stahovat ručně, jen musí být počítač připojený k internetu.

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
└── README.md               # tato dokumentace
```

## Zdroje

* Dokumentace Shapely – https://shapely.readthedocs.io/
* GEOS – https://libgeos.org/
* GeoPandas – https://geopandas.org/
* pyproj – https://pyproj4.github.io/pyproj/
* Natural Earth – https://www.naturalearthdata.com/
