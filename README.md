# mecab-ko-dic for Lindera

This repository holds the files of the
[mecab-ko-dic](https://bitbucket.org/eunjeon/mecab-ko-dic) release
2.1.1-20180720, unmodified. mecab-ko-dic is a dictionary for Korean
morphological analysis with [MeCab](https://taku910.github.io/mecab/), and
[Lindera](https://github.com/lindera/lindera) builds its Korean dictionary,
`lindera-ko-dic`, from this release. The repository exists to pin the exact
inputs of that build for reproducibility and availability, following the same
convention as [lindera/sudachidict](https://github.com/lindera/sudachidict),
[lindera/unidic-mecab](https://github.com/lindera/unidic-mecab) and
[lindera/mecab-ipadic](https://github.com/lindera/mecab-ipadic).

Current version: **2.1.1-20180720** (upstream tag
[release-2.1.1-20180720](https://bitbucket.org/eunjeon/mecab-ko-dic/src/release-2.1.1-20180720/)).

## Contents

| Files | Contents | Origin |
| --- | --- | --- |
| `*.csv` (40 files) | Lexicon: the surface form, left and right context IDs, cost and features of each entry | Release |
| `matrix.def` | Connection costs between context IDs | Release |
| `left-id.def`, `right-id.def`, `pos-id.def` | Left and right context IDs, and part-of-speech IDs | Release |
| `char.def`, `unk.def` | Character categories, and entries for unknown words | Release |
| `feature.def`, `rewrite.def`, `model.def` | Feature templates, rewrite rules, and the trained model | Release |
| `dicrc` | Dictionary configuration for MeCab | Release |
| `Makefile.am`, `Makefile.in`, `configure`, `configure.ac`, `autogen.sh`, `install-sh`, `missing`, `clean` | Files for compiling and installing the dictionary with MeCab | Release |
| `tools/` | Scripts that add user dictionaries (`add-userdic.sh`), change the part of speech of `]` in `Symbol.csv` for product search (`convert_for_using_store.sh`), and print n-best results with costs (`mecab-bestn.sh`) | Release |
| `user-dic/` | Instructions in Korean and sample entries for user dictionaries | Release |
| `AUTHORS`, `COPYING`, `INSTALL` | The authors, the Apache License 2.0, and installation instructions | Release |
| `ChangeLog`, `NEWS`, `README`, `.keep` | Empty files | Release |
| `.gitattributes` | Stores the `*.def` files in Git LFS | Lindera |
| `README.md`, `NOTICE.txt` | This file, and Lindera's attribution of mecab-ko-dic | Lindera |

The nine `*.def` files are stored with Git LFS. Install
[Git LFS](https://git-lfs.com/) before cloning to get their contents.

## Sources

Retrieved on 2026-11-16.

The release is the tarball `mecab-ko-dic-2.1.1-20180720.tar.gz`
(49,775,061 bytes). Two places serve the same file:

| Where | URL |
| --- | --- |
| Downloads of the upstream repository | <https://bitbucket.org/eunjeon/mecab-ko-dic/downloads/mecab-ko-dic-2.1.1-20180720.tar.gz> |
| Google Drive folder that the upstream README links to since 2025-06-29 | <https://drive.google.com/drive/folders/1STH9WUG7_flOjFuGIKqnmebhSfQaHbzM> (file ID `1rzCAlJ6YvJBAX9aRcIJjF7DCTD6UyEcZ`) |

| Archive | SHA-256 |
| --- | --- |
| `mecab-ko-dic-2.1.1-20180720.tar.gz` | `fd62d3d6d8fa85145528065fabad4d7cb20f6b2201e71be4081a4e9701a5b330` |

The tarball holds 72 files under `mecab-ko-dic-2.1.1-20180720/`. They are,
byte for byte, the files of this repository other than `.gitattributes`,
`README.md` and `NOTICE.txt`. To check, clone this repository into
`mecab-ko-dic` with Git LFS installed, and run the following in the directory
that holds the clone:

```shell
curl -fsSL -O https://bitbucket.org/eunjeon/mecab-ko-dic/downloads/mecab-ko-dic-2.1.1-20180720.tar.gz
echo 'fd62d3d6d8fa85145528065fabad4d7cb20f6b2201e71be4081a4e9701a5b330  mecab-ko-dic-2.1.1-20180720.tar.gz' | sha256sum -c -
tar -xzf mecab-ko-dic-2.1.1-20180720.tar.gz
diff -r -x .git mecab-ko-dic-2.1.1-20180720 mecab-ko-dic
```

The checksum matches, and `diff` names only the files that Lindera added:

```text
mecab-ko-dic-2.1.1-20180720.tar.gz: OK
Only in mecab-ko-dic: .gitattributes
Only in mecab-ko-dic: NOTICE.txt
Only in mecab-ko-dic: README.md
```

The upstream repository's source tree does not hold these files. At the tag
`release-2.1.1-20180720`, it holds the seed lexicon with zero context IDs and
costs (`seed/`), the packaging (`final/`) and tools (`utils/`), but not
`matrix.def`, `left-id.def`, `right-id.def`, `model.def` or the lexicon with
costs. `seed/build.sh` produces them with `mecab-cost-train` from a training
corpus that, as the upstream README says, cannot be distributed because of its
copyright. The release is therefore the source of these files.

## Modifications

None. The 72 files are byte-identical to the release. Lindera added
`.gitattributes`, `README.md` and `NOTICE.txt`.

## Use in Lindera

`lindera-ko-dic` downloads
<https://lindera.dev/mecab-ko-dic-2.1.1-20180720.tar.gz> and checks its
SHA-256, `702ced21c6167e9d9aebc674ab5ee54af58d4443975f2940d37d0567c020591a`, in
[`lindera-ko-dic/build.rs`](https://github.com/lindera/lindera/blob/main/lindera-ko-dic/build.rs).
That tarball holds, byte for byte, the files of this repository other than
`README.md` and `NOTICE.txt`.

To build the dictionary, see
[Build](https://lindera.github.io/lindera/lindera-ko-dic/build.html) in the
Lindera documentation.

## Licenses

- mecab-ko-dic is distributed under the Apache License 2.0 (`COPYING`, the same
  file as the upstream `COPYING`). Its authors are listed in `AUTHORS`.
- The upstream README states that mecab-ko-dic may be used and redistributed
  under the Apache License 2.0, and that its training corpus and part of its
  lexicon come from the results of the 21st Century Sejong Project. The
  training corpus is not part of the release or of this repository.
- `NOTICE.txt` gives Lindera's attribution of mecab-ko-dic. The release has no
  NOTICE file.

This repository is not affiliated with or endorsed by the authors of
mecab-ko-dic.
