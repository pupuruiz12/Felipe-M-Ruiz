### Ola Sou felipe Ruiz 🖖🏾
💻 Desenvolvedor Full Stack e Backend Java

🌐 Apaixonado por transformar ideias em código e criar soluções inovadoras. Atualmente, explorando o universo Full Stack e aprimorando minhas habilidades no desenvolvimento Backend com Java.

🚚 Logística + Tecnologia: Integro meu conhecimento em logística com minha expertise técnica para otimizar processos e criar soluções eficientes.
<div>
  <a href="https://github.com/pupuruiz12">
    <img height="180em" src="https://github-readme-stats.vercel.app/api?username=pupuruiz12&show_icons=true&theme=dracula&include_all_commits=true&count_private=true"/>
  </a>

  <a href="https://github.com/pupuruiz12">
    <img height="180em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=pupuruiz12&layout=compact&langs_count=16&theme=dracula"/>
  </a>
</div>

<div style="display: inline_block"><br>
  <img align="center" alt="fe-Js" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-plain.svg">
  <img align="center" alt="fe-Ts" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/typescript/typescript-plain.svg">
  <img align="center" alt="fe-React" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original.svg">
  <img align="center" alt="fe-HTML" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original.svg">
  <img align="center" alt="fe-CSS" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original.svg">
</div>

##

<divi>
  <a href="https://instagram.com/felipemateusruiz" target="_blank"><img src="https://img.shields.io/badge/-Instagram-%23E4405F?style=for-the-badge&logo=instagram&logoColor=white" target="_blank"></a>
 <a href="https://discord.gg/ruiz#9015" target="_blank"><img src="https://img.shields.io/badge/Discord-7289DA?style=for-the-badge&logo=discord&logoColor=white" target="_blank"></a> 
  <a href = "felipepupu12@gmail.com"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>
  <a href="https://www.linkedin.com/in/https://www.linkedin.com/in/felipe-ruiz-595b5022a?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=ios_app " target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a> 
  
</divi>
# GitHub Action for generating a contribution graph with a snake eating your contributions.

# ![snake gif](https://github.com/your-user-name/your-user-name/blob/output/github-contribution-grid-snake.gif)

name: Generate Snake

# Controls when the action will run.
on:
  schedule:
      # every 12 hours
    - cron: "0 */12 * * *"

  # This command allows us to run the Action automatically from the Actions tab.
  workflow_dispatch:
  
  # Also run on every push on the master branch
  push:
    branches:
    - main

# The sequence of runs in this workflow:
jobs:
  # This workflow contains a single job called "build"
  build:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
      - name: Clone repo
        uses: actions/checkout@v3
    
      - name: Generate the snake files in './dist/'
        uses: Platane/snk@v3
        id: snake-gif
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.gif
            dist/github-contribution-grid-snake.svg
        env:
           GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

      - name: Show build status
        run: git status

      - name: Push new files to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
          commit_message: Update snake animations
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

