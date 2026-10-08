<a href="https://github.com/darshanmhulagur-coder">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1000&color=F75C7E&center=true&vCenter=true&width=435&lines=Hi+There!+Iam+Darshan%F0%9F%90%8B;CSE+Student;Building+Cool+Projects" alt="Typing SVG" />
</a>
<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=1,2,5,8,20&height=200&section=header&text=Welcome%20to%20my%20Profile&fontSize=40&fontAlignY=35" width="100%" />
<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=js,ts,react,nextjs,nodejs,python,docker,git" />
  </a>
</p>
<p align="center">
  <!-- GitHub Streak Stats -->
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=darshanmhulagur-coder&theme=dark" alt="GitHub Streak" />
</p>

<p align="center">
  <!-- Top Languages -->
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=darshanmhulagur-coder&layout=compact&theme=dark" alt="Top Languages" />
</p>
![Header Animation](./assets/header-animation.gif)
name: Generate Snake Contribution Animation

on:
  # Run automatically every 24 hours
  schedule:
    - cron: "0 0 * * *"
  
  # Allows manual triggering from the Actions tab
  workflow_dispatch:

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    
    steps:
      # Generates the snake game SVGs from your contribution graph
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      # Pushes the generated SVGs to the 'output' branch
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

