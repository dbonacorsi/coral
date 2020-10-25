## Getting started

Download and unpack the Edge TPU runtime:

```
curl -O https://dl.google.com/coral/edgetpu_api/edgetpu_runtime_20200728.zip
unzip edgetpu_runtime_20200728.zip
```

Install the Edge TPU runtime:

```
cd edgetpu_runtime
sudo bash install.sh
```

The installation script will ask whether you want to enable the maximum operating frequency. Running at the maximum operating frequency increases the inferencing speed but also increases power consumption and causes the USB Accelerator to become very hot. If you're not certain your application requires increased performance, you should type "N" to use the reduced operating frequency.

You can read more about the performance setting in the USB Accelerator datasheet.

Now connect the USB Accelerator to your computer using the provided USB 3.0 cable.

Then continue to install the TensorFlow Lite library.

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/dbonacorsi/coral/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
