# 如何将lectures, labs, projects仓库合并入CSCI0300-s24仓库

以将CSCI0300-s24-lectures合并入CSCI0300-s24为例:

1. 添加lectures仓库作为远程仓库

```
git remote add lectures https://github.com/Oooscar8/CSCI0300-s24-lectures.git
```

2. 获取lectures仓库的所有分支

```
git fetch lectures
```

3. 创建一个新的分支用于合并

   创建并切换到一个新的分支来处理合并：

```
git checkout -b merge-lectures
```

4. 将lectures仓库的分支合并到目标仓库的新分支中

   使用 `git merge` 命令，将lectures仓库的 `main` 分支合并到当前分支中，同时保留历史记录：

```
git merge lectures/main --allow-unrelated-histories
```

5. 将lectures仓库的内容移动到CSCI0300-s24仓库的CSCI0300-s24-lectures文件夹

   创建CSCI0300-s24-lectures文件夹并移动内容：

   ```
   mkdir -p CSCI0300-s24-lectures
   git mv * CSCI0300-s24-lectures/（*可能需要替换成除CSCI0300-s24-lectures文件夹以外的文件）
   ```

   如果lectures仓库中有隐藏文件（如 `.gitignore`），需要单独移动这些文件：

   ```
   git mv .gitignore CSCI0300-s24-lectures/
   ```

6. 提交移动操作

```
git commit -m "Moved CSCI0300-s24-lectures to CSCI0300-s24."
```

7. 推送合并后的结果

   推送合并后的内容到CSCI0300-s24仓库的远程分支：

   ```
   git push origin merge-lectures
   ```

   如果确认合并正确，将合并结果合并回 `main` 分支：

   ```
   git checkout main
   git merge merge-lectures
   git push origin main
   ```

同理可以merge CSCI0300-s24-labs 和 CSCI0300-s24-projects。

