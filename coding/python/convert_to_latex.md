## Converting jupyter notebook to latex

- conda install -c conda-forge pandoc
- pip install --upgrade pandoc
- jupyter nbconvert --to markdown <jupyter.ipynb>
- pandoc -f markdown -t latex <filename>.md -o filename.tex
- cp filename.tex <overleaf_git_folder>