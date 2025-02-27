# Converting Jupyter Notebooks to LaTeX for Overleaf

This guide provides step-by-step instructions to convert a Jupyter notebook into a LaTeX file, making it easy to upload to Overleaf for further editing and collaboration.

---

## Steps to Convert a Jupyter Notebook to LaTeX

1. **Install Pandoc via Conda** 

    Pandoc is a tool that facilitates format conversions, including Markdown to LaTeX. First, install Pandoc through Conda:

    \`\`\`bash
    conda install -c conda-forge pandoc
    \`\`\`

2. **Upgrade Pandoc (if needed)**

    To ensure Pandoc is up to date, use the following command:

    \`\`\`bash
    pip install --upgrade pandoc
    \`\`\`

3. **Convert Jupyter Notebook to Markdown**

    Use `nbconvert` to convert your Jupyter notebook (`<jupyter.ipynb>`) to Markdown:

    \`\`\`bash
    jupyter nbconvert --to markdown <jupyter.ipynb>
    \`\`\`

    - **Output**: This command generates a Markdown file (`<filename>.md`) from your notebook.

4. **Convert Markdown to LaTeX with Pandoc**

    Convert the generated Markdown file to LaTeX format:

    \`\`\`bash
    pandoc -f markdown -t latex <filename>.md -o <filename>.tex
    \`\`\`

    - **`-f markdown`**: Specifies the input format as Markdown.
    - **`-t latex`**: Specifies the output format as LaTeX.
    - **`-o <filename>.tex`**: Defines the name of the output file in LaTeX format.

5. **Copy LaTeX File to Overleaf Project Folder**

    Move the generated `.tex` file to your Overleaf Git folder for direct syncing or uploading to Overleaf:

    \`\`\`bash
    cp <filename>.tex <overleaf_git_folder>
    \`\`\`

    - **Note**: Replace `<overleaf_git_folder>` with the path to your Overleaf Git folder or project location.

---

## Additional Notes

- **Image and Resource Files**: If your Jupyter notebook contains images or additional files, ensure they are copied alongside the `.tex` file, as these resources are necessary for a complete document in Overleaf.
- **Overleaf Integration**: For seamless syncing, you can use Overleaf’s Git integration to directly push files from your local Git repository.
- **Alternative Output Formats**: Instead of LaTeX, Pandoc supports many output formats, such as PDF and DOCX, by adjusting the `-t` parameter.

By following these steps, you can convert Jupyter notebooks to LaTeX and efficiently integrate them with Overleaf for collaborative LaTeX editing.
