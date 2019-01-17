# Transparencies

Scribus has no issues with transparencies in your files, but it cannot flatten them.

If your print shop has asked for a file without transparencies here is what you can do:

- Avoid using transparencies.
- Find a print shop that correctly prints PDF 1.4 with transparencies.
- Use ghostscript to create a (CMYK) PDF with flattened transparencies.
- Use the full version of Acrobat (or another pre-press tool) to flatten the PDF created by Scribus.

## The issue with transparencies

Nowadays, every home and office printer can handle PDFs with transparencies.

But Print Shops often refuse PDFs with transparencies. Sometimes, they do not even specify it, and still simply "ignore" the transparencies in your file.

Why is it like this? Every Print Shop has the software needed for correctly flattening your PDFs and it won't be much work (if any) for them to accept PDF files with transparencies. The most likely reason why the refuse to do so, is that every change they do to the PDF might got wrong and they don't want to be liable for it. And since Adobe products can flatten the transparencies, Print Shops do not see a reason for changing their policy.

## Flattening transparencies

### Using ghostscript

The following command should give you a flattened pdf 1.3 but thext is not selectable anymore:

```sh
gs -o test-transparencies-1.3.pdf \
   -sDEVICE=pdfwrite        \
   -dCompatibilityLevel=1.3 \
    test-transparencies-1.4.pdf
```

- The text gets rasterized.

```sh
   -dEmbedAllFonts=true \
   -dSubsetFonts=true \
```

but it did not at making the text selectable again.
