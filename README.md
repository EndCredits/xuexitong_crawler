# 超星学习通作业爬取工具

哈哈哈哈没想到吧，这个项目还能有续集！超星学习通爬取课后题小工具正式发布 v0.0.1

## ⚠ 注意事项

1. 这个工具主要用于爬取**已经完成**的课后题作业，**未完成的作业是无法获取到正确答案的**。获取到之后会生成 Word 版本的习题，分为带答案版和不带答案版，方便同学们进行背诵复习和重做，以进一步查缺补漏
2. **"泛雅课堂", "超星学习通"等均为北京世纪超星信息技术发展有限责任公司的商标**
3. **本项目应只作为学习交流目的使用，禁止任何形式的商用和侵犯北京世纪超星信息技术发展有限责任公司的行为。若内容侵权，请立即联系作者 (me@leemina.moe) 进行删除**

## ✨ 特性

1. 支持将题目导出为 Markdown, Word (由 python-docx 强力驱动), json 格式 
2. 全流程模拟正常浏览器行为，避免被检测封号
3. 没了

## 🥳开始使用

考虑到使用 Windows 的人较多，故先提供 Windows 版本的教程

1. 首先从微软应用商店安装 [Windows Terminal](https://apps.microsoft.com/detail/9n0dx20hk701)

2. 以管理员权限运行 Windows 终端

3. 解除外部脚本运行限制

	```Powershell
	Set-ExecutionPolicy bypass
	```

4. 新建文件夹避免污染

    ```Powershell
    mkdir .\Miniconda_installer
    cd .\Miniconda_installer
    ```

4. 安装 Miniconda

    纯属个人习惯，如果你有用的顺手的包管理器也可以

    ```Powershell
    Invoke-WebRequest "https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe" -OutFile ".\miniconda_installer.exe"

    Start-Process -FilePath ".\miniconda_installer.exe" -ArgumentList "/S" -Wait

    # 按照提示一路下一步

    Remove-Item .\miniconda_installer.exe
    ```

5. 启动 conda 环境

    在开始菜单里找到 "Anaconda Powershell Prompt (miniconda3)" 并运行，会得到一个命令行窗口

6. 创建 conda 环境并安装依赖

    ```Powershell
    # 为避免找不到输出，这里放在桌面上
    cd ~\Desktop\
    mkdir .\fanya
    # 完成这一步后你应该能在桌面上找到一个 fanya 文件夹

    # 在国内使用 JsDelivr 镜像
    cd .\fanya
    Invoke-WebRequest "https://cdn.jsdelivr.net/gh/EndCredits/xuexitong_crawler@main/environment.yml" -OutFile .\environment.yml

    # 从 environment 文件创建 conda 环境
    conda env create -f environment.yml -n fanya
    ```

7. 开始使用

    ```Powershell
    # 激活虚拟环境
    conda activate fanya

    # 下载本程序
    Invoke-WebRequest "https://cdn.jsdelivr.net/gh/EndCredits/xuexitong_crawler@main/main.py" -OutFile .\main.py

    # 查看示例用法
    python .\main.py -h

    # 默认会导出 Markdown, Word, JSON 三种格式的文件，不过对于大多数人 Word 已足够
    python .\main.py --format word <phone numebr> <password>
    ```

## 🔨 Development (Code of Conduct)

1. Please use the coding style recommended by PEP8 to format your code

## ⏳ TODO 

 - ⭕ 实现 WebUI 并托管
 - ⭕ 适配更多题型
 - ⭕ 实现题库接口，自动搜索未完成题目的答案
