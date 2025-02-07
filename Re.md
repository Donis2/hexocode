name: 柳溪斋

on:
  push:
    branches: [main, master]
    paths:
      - '*.json'
      - '**.yml'
      - '**/source/**'

jobs:
  blog:
    timeout-minutes: 30
    runs-on: ubuntu-latest

    steps:
      # 检出代码
      - uses: actions/checkout@v3
        name: Checkout code

      # 设置 Node.js 版本
      - uses: actions/setup-node@v3
        with:
          node-version: '18'

      # 缓存 Node.js 依赖
      - name: Cache node_modules
        uses: actions/cache@v3
        with:
          path: node_modules
          key: ${{ runner.os }}-node-modules-${{ hashFiles('**/package-lock.json') }}
          restore-keys: |
            ${{ runner.os }}-node-modules-

      # 安装依赖
      - name: Install dependencies
        run: |
          npm install
          npm install hexo-butterfly-tag-plugins-plus --save
          echo "Dependencies installed successfully."

      # 安装 Hexo-cli
      - name: Install Hexo-cli
        run: |
          npm install -g hexo-cli --save
          echo "Hexo CLI installed successfully."

      # 初始化子模块
      - name: Initialize submodules
        run: |
          git submodule sync
          git submodule update --init --recursive
          echo "Submodules initialized successfully."

      # 清理部署目录
      - name: Clean deploy folder
        run: |
          rm -rf .deploy_git
          echo ".deploy_git folder cleared."

      # 编译博客
      - name: Build Blog
        run: |
          hexo clean
          hexo generate --debug
          echo "Blog build process completed."







      # - name: 部署到Github
      #   with:
      #     token: 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
      #     repository-name: Donis2/donis2.github.io
      #     branch: main
      #     folder: public
      #     commit-message: "${{ github.event.head_commit.message }} Updated By Github Actions"



      # # 部署博客
      # - name: Deploy Blog
      #   env:
      #    DEPLOY_TOKEN: ${{ secrets.GH_TOKEN }}   # 从 GitHub Secrets 读取 Token
      #   run: |
      #    git config --global user.name "Donis2"
      #    git config --global user.email "2561055937@qq.com"
      #    npx hexo deploy --debug



      - name: 部署博客
        run: 
          hexo clean && hexo g
          cd -
          git config user.name "${{secrets.GIT_NAME}}"
          git config user.email "${{secrets.GIT_EMAIL}}"
          git init
          git add .
          git commit -m "Update"
          git push --force --quiet "https://${{secrets.GH_TOKEN}}@${{secrets.GH_REF}}" main:main
         # git push --force --quiet "https://${{secrets.CD_TOKEN}}@${{secrets.CD_REF}}" main:main




     

      
      # 部署成功
      - run: echo "Deploy Successful!"
