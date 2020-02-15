```bash
git init --bare .
```

echo 'hello' | git hash-object -t blob --stdin -w
git hash-object -t blob temp-file -w
| cat - ./objects/ce/013625030ba8dba906f756967f9e9ca394464a \
git cat-file blob ce01
git show ce01
| git hash-object -t tree --stdin -w
100644 blob ce013625030ba8dba906f756967f9e9ca394464a$(printf '\t')name.ext
100755 blob ce013625030ba8dba906f756967f9e9ca394464a$(printf '\t')name2.ext
| cat - ./objects/58/417991a0e30203e7e9b938f62a9a6f9ce10a9a \
git cat-file tree 5841 | xxd
git ls-tree 5841
git show 5841
git hash-object -t commit --stdin -w <<EOF
git commit-tree 5841 -p d4da << EOF
| cat - ./objects/ef/d4f82f6151bd20b167794bc57c66bbf82ce7dd \
git cat-file commit efd4
git show efd4~
# 找到commit efd4对应的tree：
# 注意：运行结果与手动写efd4^{tree}无异
git ls-tree efd4
# 找到commit efd4（对应的tree）的/name.ext：
git ls-tree efd4 -- name.ext
# 找到commit efd4对应的tree：
# 注意：运行结果与只写efd4有本质差异
git show efd4^{tree}
# 找到commit efd4（对应的tree）的/name.ext：
git show efd4:name.ext
注意：你可以让tag指向tag，虽然没有什么卵用

- Lv2
```bash
git mktag <<EOF
object efd4f82f6151bd20b167794bc57c66bbf82ce7dd
type commit
tag simple-tag
tagger b1f6c1c4 <b1f6c1c4@gmail.com> 1527189535 +0000

The tag message
EOF
```

*特别注意：`git tag -a`命令不仅仅创建了tag对象，还建立了新的引用在`refs/tags/the-tag`。*
GIT_AUTHOR_NAME=b1f6c1c4 \
GIT_AUTHOR_EMAIL=b1f6c1c4@gmail.com \
GIT_AUTHOR_DATE='1600000000 +0800' \
GIT_COMMITTER_NAME=b1f6c1c4 \
GIT_COMMITTER_EMAIL=b1f6c1c4@gmail.com \
git tag -a -m 'The tag message' the-tag efd4:name.ext
git rev-parse the-tag
git cat-file tag 9cb6
git cat-file blob 9cb6
git show 9cb6
  - `git mktag` - 创建tag
  - `git cat-file <type> <SHA1>` - 查看blob和commit和tag