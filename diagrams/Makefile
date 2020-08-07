.PHONY: all clean

CURDIR := $(shell pwd)

core_find = $(if $(wildcard $1),$(shell find $(1:%/=%) -type f -name $(subst *,\*,$2)))

SOURCE_MMD := $(sort $(foreach pat,*.mmd,$(call core_find,$(CURDIR)/,$(pat))))
OUTPUT_MMD_SVG = $(addsuffix .svg, $(basename $(SOURCE_MMD)))
OUTPUT_MMD_PDF = $(addsuffix .pdf, $(basename $(SOURCE_MMD)))
SOURCE_SVG := $(filter-out $(OUTPUT_MMD_SVG),$(sort $(foreach pat,*.svg,$(call core_find,$(CURDIR)/,$(pat)))))
OUTPUT_SVG_PDF = $(addsuffix .pdf, $(basename $(SOURCE_SVG)))

all: $(OUTPUT_MMD_SVG) $(OUTPUT_MMD_PDF) $(OUTPUT_SVG_PDF)

clean::
	rm -f $(OUTPUT_MMD_PDF)
	rm -f $(OUTPUT_SVG_PDF)

%.svg: %.mmd
	npx mmdc -p puppeteer-config.json --input $< --output $@ -c config.json

# %.pdf: %.svg
# 	cairosvg $< --output $@

%.pdf: %.svg
	npx svgexport $< $@
