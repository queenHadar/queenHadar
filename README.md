### Hi,  my name is Hadar 
🦋 🌈 ☁️ 🌻 💗

---
### Languages and Tools:

<img align="left" alt="Visual Studio Code" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" style="padding-right:10px;" />
<img align="left" alt="HTML5" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" style="padding-right:10px;" />
<img align="left" alt="CSS3" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" style="padding-right:10px;" />
<img align="left" alt="JavaScript" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" style="padding-right:10px;" />
<img align="left" alt="React" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" style="padding-right:10px;" />
<img align="left" alt="Node.js" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" style="padding-right:10px;" />
<img align="left" alt="MongoDB" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mongodb/mongodb-original.svg" style="padding-right:10px;" />
<img align="left" alt="Git" width="26px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" style="padding-right:10px;" />
<img align="left" alt="GitHub" width="26px" src="https://user-images.githubusercontent.com/3369400/139448065-39a229ba-4b06-434b-bc67-616e2ed80c8f.png" style="padding-right:10px;" />
<img align="left" alt="Docker" width="45px" src="https://developers.redhat.com/sites/default/files/styles/article_feature/public/blog/2015/01/docker-whale-home-logo.png?itok=nf2cLFMc" style="padding-right:10px;" />
<img align="left" alt="Python" width="32px" src="https://user-images.githubusercontent.com/125987820/231272066-5a3f5d8b-2d66-43df-8511-28d8631a3751.png" style="padding-right:7px;" />
<img align="left" alt="c#" width="55px" src="https://www.codeguru.com/wp-content/uploads/2021/08/C-Sharp-Tutorials.png" style="padding-right:7px;" />
<img align="left" alt="Linux" width="30px" src="https://cdn-icons-png.flaticon.com/512/6124/6124995.png" style="padding-right:7px;" />

<br/>
<br/>

--- 
name: Test
on:
  push:
    branches:
      - master
  workflow_dispatch:
  schedule:
    - cron: "0 0 * * *"
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: |
          git config --global user.email "41898282+github-actions[bot]@users.noreply.github.com"
          git config --global user.name "github-actions[bot]"
      - uses: qhy040404/am-update-time@master
        with:
          playlist: 'https://music.apple.com/cn/playlist/just-my-favorite/pl.u-8aAVZglHWya2xM'
          keyword: 'Last Update: '
      - run: |
          cat README.md
      - name: Commit changes
        shell: sh
        run: |
          set -eu
          git add README.md
          if ! git diff --cached --quiet; then
              git commit -m "Update playlist"
          fi
      - name: Push changes
        uses: ad-m/github-push-action@v0.6.0
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          branch: ${{ github.ref }}
