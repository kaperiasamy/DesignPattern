## **1. `jp2a`** (JPEG/PNG to ASCII)

* A command-line tool that converts images to ASCII art.
* Supports color output and scaling.

**Install:**

```bash
sudo apt update
sudo apt install jp2a
```

**Usage:**

```bash
jp2a image.jpg
```

or with colors:

```bash
jp2a --colors image.jpg
```

You can also output to a file:

```bash
jp2a image.jpg --output=ascii.txt
```

---

## **2. `caca-utils` (`img2txt`)**

* From the **libcaca** package, converts images to ASCII in the terminal.

**Install:**

```bash
sudo apt install caca-utils
```

**Usage:**

```bash
img2txt image.png
```

---

## **3. `ascii-image-converter`** (modern, supports PNG/JPG/GIF)

* More modern and actively maintained.

**Install via Snap:**

```bash
sudo snap install ascii-image-converter
```

**Usage:**

```bash
ascii-image-converter image.jpg
```

---

## **4. Online tools (if CLI not needed)**

* **[https://www.text-image.com/](https://www.text-image.com/)** (simple drag-and-drop)
* **[https://ascii-art-generator.org/](https://ascii-art-generator.org/)**

---

💡 **Tip:** If your images are too detailed, reduce resolution before converting — ASCII art works best with simpler shapes and fewer colors. You can use:

```bash
convert image.jpg -resize 80x80 small.jpg
```

(using `ImageMagick`, install with `sudo apt install imagemagick`).
