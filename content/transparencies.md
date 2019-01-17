# Transparencies

## The issue with transparencies

## Flattening transparencies

### Using ghostscript

The following command should give you a flattened pdf 1.3 but thext is not selectable anymore:

```sh
gs -o test-transparencies-1.3.pdf \
   -sDEVICE=pdfwrite        \
   -dCompatibilityLevel=1.3 \
    test-transparencies-1.4.pdf
```

I've tried adding

```sh
   -dEmbedAllFonts=true \
   -dSubsetFonts=true \
```

but it did not at making the text editable again.
