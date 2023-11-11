# SW8-Documentation

Documentation for SeaWolf VIII


## Required Tools

Documentation is generated using [mkdocs](https://www.mkdocs.org/) using the [mkdocs-material](https://squidfunk.github.io/mkdocs-material/) theme.

- Install Python3 (executable may just be named `python` on windows)
- Run the following command
    ```sh
    python3 -m pip install -U -r requirements.txt
    ```

## Preview Documentation

- In this folder run the following command

```sh
mkdocs serve
```


## Publishing documentation

**WARNING: Running this command will make the documentation public without prompts!**

```sh
mkdocs gh-deploy
```


## Folder Structure & Practices

- Each subteam gets a folder in docs. Each will contain an img subfolder for images
- Each subteam's folder can have subfolders if desired, or just a collection of pages
- Site organization is defined by nav tree in `mkdocs.yml`. Edit this tree to control page order and titles.
- Do not use H1 headers (`# Text`). The page's title is determined by the `mkdocs.yml` nav tree.
- Top level img folder is for site images, not images used in docs
- Each subteam should have an `img` and `diagram` folder for images and diagrams (drawio / diagrams.net).
- Using `jpg` / `jpeg` images is HIGHLY recommended over `png` images. If using `png` images, consider using `pngquant` to compress them first.
- Diagrams should be generated using drawio / diagrams.net (use desktop app). Store the source files in `diagram` folders (in each subteam's folder). When exporting a jpg / png, place it in the `img` folder. Use the same name as the diagram source. For larger diagrams, it is probably best to render at 200% zoom.
- Images in markdown (these are custom features not standard markdown)
    - To choose image size, use attribute list `![](path/to/image){: style="width:80%;height:50%"}`. Either width, height, or both can be used.
    - To center an image, add the `center` class to the attribute list `{: .center}`
    - To prevent zoom on click add the `img-nozoom` attribute `{: img-nozoom }`
- Videos
    - NEVER add videos to the git repo
    - Upload the video to the club google drive and share it publicly and add the html google drive generates to embed it (three dots menu, open in new windows, three dots menu again, embed item).
    - You could also upload it to the club's youtube (probably unlisted) and embed it using youtube generated html