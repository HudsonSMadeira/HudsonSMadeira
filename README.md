main.yml

name: Pacman Animation

on:
  workflow_dispatch:
  schedule:
    - cron: "0 */6 * * *"

jobs:
  generate:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v4

      - name: Generate Pacman
        uses: abozanona/pacman-contribution-graph@main
        with:
          github_user_name: ${{ github.repository_owner }}

      - name: Organize files
        run: |
          mkdir -p output
          mv dist/*.svg output/
          echo "Arquivos gerados:"
          ls -la output/

      - name: Update README
        run: |
          SVG_LIGHT="https://raw.githubusercontent.com/${{ github.repository }}/output/pacman-contribution-graph.svg?t=$(date +%s)"
          SVG_DARK="https://raw.githubusercontent.com/${{ github.repository }}/output/pacman-contribution-graph-dark.svg?t=$(date +%s)"
          
          HTML_CONTENT="<div align=\"center\">\n<picture>\n  <source media=\"(prefers-color-scheme: dark)\" srcset=\"$SVG_DARK\">\n  <source media=\"(prefers-color-scheme: light)\" srcset=\"$SVG_LIGHT\">\n  <img src=\"$SVG_LIGHT\" alt=\"Pacman eating contributions\" width=\"100%\">\n</picture>\n</div>"
          
          # Remove qualquer conteúdo existente do Pacman
          sed -i '/<div align="center">/,/<\/div>/d' README.md
          
          # Adiciona o novo conteúdo no final
          echo -e "\n$HTML_CONTENT" >> README.md
          
          git config user.name "GitHub Actions"
          git config user.email "actions@github.com"
          git add .
          git commit -m "Update Pacman animation [skip ci]"
          git push
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}




readme:

<h2 align="left">Olá 👋! Meu nome é Hudson... E eu sou um..., Analista e  Desenvolvedorde Sistema....</h2>

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=HudsonSMadeira&hide_title=false&hide_rank=false&show_icons=true&include_all_commits=true&count_private=true&disable_animations=false&theme=dracula&locale=en&hide_border=false" height="150" alt="stats graph"  />
  <img src="https://github-readme-stats.vercel.app/api/top-langs?username=HudsonSMadeira&locale=en&hide_title=false&layout=compact&card_width=320&langs_count=5&theme=dracula&hide_border=false" height="150" alt="languages graph"  />
</div>

###

<h3 align="left">🛠 Linguagem e ferramentas</h3>

###

<div align="center">
  <img src="https://skillicons.dev/icons?i=ts" height="60" alt="typescript logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=nextjs" height="60" alt="nextjs logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=tailwind" height="60" alt="tailwindcss logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=html" height="60" alt="html logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=css" height="60" alt="css logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=react" height="60" alt="react logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=django" height="60" alt="django logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=nodejs" height="60" alt="nodejs logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=js" height="60" alt="js logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=py" height="60" alt="python logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=java" height="60" alt="java logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=c" height="60" alt="c logo"  />
</div>
</div>

###

###

<h3 align="left">🔥   Minhas estatísticas:</h3>

###

<div align="center">
  <img src="https://streak-stats.demolab.com?user=HudsonSMadeira&locale=en&mode=daily&theme=dracula&hide_border=false&border_radius=5&order=3" height="150" alt="streak graph"  />
</div>

###

###


<div align="center">
  <a href="https://www.linkedin.com/in/hudson-madeira-2a6b47239/" target="_blank">
    <img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="linkedin logo" />
  </a>
  <a href="https://www.youtube.com/@hudsonsilvamadeira2818" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Youtube&logo=youtube&label=&color=FF0000&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="youtube logo" />
  </a>
  <a href="https://hudson-website.vercel.app/" target="_blank">
    <img src="https://img.shields.io/static/v1?message=WebSite&logo=website&label=&color=1DA1F2&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="twitter logo" />
  </a>
</div>

###

###
<!-- PACMAN_WILL_APPEAR_HERE -->
<img src="https://raw.githubusercontent.com/HudsonSMadeira/HudsonSMadeira/main/output/pacman-contribution-graph-dark.svg?t=1">

###

<div align="center">
  <img src="https://visitor-badge.laobi.icu/badge?page_id=HudsonSMadeira.HudsonSMadeira&"  />
</div>
