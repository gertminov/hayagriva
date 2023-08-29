# Hayagriva

> Modified version of [hayagriva](https://github.com/typst/hayagriva) that replaces the chicago-author-date style with APA style text citations.

## Modifications
- `#cite(key)` now returns APA style text citations
    - "," after author names (Lastname 2023) => (Lastname, 2023)
    - "et al." after 3+ authors (Lastname1, Lastname2, Lastname3 2023) => (Lastname1, et al., 2023)
    - "and" replaced by "&" (Lastname1 and Lastname2 2023) => (Lastname1 & Lastname2, 2023)

All that is happening inside the `src/style/chicago/author_date.rs` and the `src/style/chicago/mod.rs` files.
So hayagriva still thinks it is using the chicago style.

I know to little rust to make a propper implementation, but i need APA citations for my bachelor thesis. 

## How to use

If you also want apa citations in your typst, you have two options:
1. if you are on windows you can download the modified exe from the repo [typst.exe](typst.exe) (hit the download button in the right corner)
2. [compile typst yourself](#compile-yourself) with the modified version of hayagriva. (If you have never done this, me neither, but it's quite simple)

### Compile yourself
You need:
- [rust](https://www.rust-lang.org/tools/install)
- (on windows)  [Visual studio Build tools](https://visualstudio.microsoft.com/de/downloads/)
    - You have to download the community version, then select that you want to install the build tools in the installer and than select the "Desktopt development with C++" workload.
    - If you are on linux or mac just try to build the project the rust compiler will give some useful tips I hope (at least it does on windows).
- git

#### Steps
1. Clone the typst repo into a folder of your choice
    ```bash
    git clone https://github.com/typst/typst.git
    ```
2. tell rust where to find the modified version of hayagriva
    1. go into the folder where you cloned typst
    2. open the file `Cargo.toml` with a text editor
    3. add the following line to the end of that file
        ```toml
        [patch.crates-io]
        hayagriva = { git = 'https://github.com/gertminov/hayagriva.git' }
        ```
3. build typst
    ```bash
    cargo build --release
    ```
4. the compiled binary is now in the `target/release` folder
    - on windows it is called `typst.exe`
    - on linux and mac it is called `typst`
    
    you can use that exe like the original one:
    ```bash
    typst compile my_file.typ
    ```

If you have any questions feel free to open an issue