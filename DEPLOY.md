# Deploy — perfil GitHub de mrflippermen

Repo destino: **`github.com/mrflippermen/mrflippermen`** (repo con tu nombre = se ve en tu perfil).

## Subir (y listo — todo renderiza al instante, sin GitHub Actions)
```bash
cd flippermen-profile
git init
git add .
git commit -m "GitHub profile — Red Team edition"
git branch -M main
git remote add origin https://github.com/mrflippermen/mrflippermen.git
git push -u origin main
```

Todas las imágenes del README salen inmediatamente tras el push: banner (dark/light
desde `main`), badges/shields, skill-icons, stats/lenguajes/streak (servicios en vivo)
y los badges de stars/último-commit por repo. **No hay que activar nada ni crear ramas.**

## Banner animado en TODOS lados
El README usa `banner.gif` (foto→logo en loop). Un GIF anima en la web **y en la app móvil** de GitHub, sin depender del proxy camo ni de SMIL.
Regenerar el GIF: `python3 .github/scripts/make_gif.py` (necesita `pip install cairosvg pillow`).

## Estructura
```
README.md                            perfil Red Team (autocontenido)
dark.svg / light.svg                 banner terminal + retrato 1-bit de tu foto (camo-safe)
assets/portrait-src.png              foto fuente
.github/scripts/generate_banner.py   herramienta local: foto -> retrato + logo (cubo Flippermen) en el VISUAL.MAP, en loop
```

## Regenerar el banner si cambias la foto
```bash
python3 .github/scripts/generate_banner.py assets/portrait-src.png dark.svg light.svg --cols 200
```
`--cols` sube/baja la densidad. El retrato queda visible en estático (no depende de la
animación), así el proxy de GitHub (camo) no lo corta.

## Paleta Red Team
Fondo `#0A0E14` · verde terminal `#39FF14` · rojo `#FF3B30` · violeta de apoyo `#A78BFA`.

## Nota
Los badges de stars/último-commit por repo usan la API pública vía shields.io: si un repo
no existe con ese nombre exacto, ese badge saldrá vacío — ajusta la URL en `README.md`.
