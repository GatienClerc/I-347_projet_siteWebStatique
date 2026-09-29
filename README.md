# I-347_projet_siteWebStatique

## installation

cd chemin
docker compose up -d
docker run --rm -v web_data:/destination -v "%cd%\web:/source:ro" alpine sh -c "cp -a /source/. /destination/"
http://localhost:80