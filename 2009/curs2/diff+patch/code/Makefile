DIST := diff_u.tex diff_c.tex diff_no_params.tex
PATCH_FILES := $(patsubst %.tex, %.patch, $(DIST))
HIGHLIGHT_OPTS = -L -f -t 8 -c highlight.sty

ORIGINAL_FILE = f_original.txt
MODIFIED_FILE = f_modificat.txt
UPDATED_FILE  = f_actualizat.txt
SOURCE_FILES := $(ORIGINAL_FILE) $(MODIFIED_FILE)
TXT_FILES    := $(SOURCE_FILES) $(UPDATED_FILE)
TEX_FILES   := $(DIST) $(patsubst %.txt, %.tex, $(TXT_FILES))
DIFF := diff --label=$(ORIGINAL_FILE) --label=$(MODIFIED_FILE)

all: $(TEX_FILES)

$(UPDATED_FILE): $(ORIGINAL_FILE) $(PATCH_FILES)
	patch $< -i diff_u.patch -o $@

%.tex: %.patch
	highlight $(HIGHLIGHT_OPTS) -l -i $< -o $@
%.tex: %.txt
	highlight $(HIGHLIGHT_OPTS) --syntax=txt -i $< -o $@
# make diff files
diff_u.patch: $(SOURCE_FILES)
	$(DIFF) -u $^ > $@ || true
diff_c.patch: $(SOURCE_FILES)
	$(DIFF) -c $^ > $@ || true
diff_no_params.patch: $(SOURCE_FILES)
	$(DIFF)    $^ > $@ || true


.PHONY: clean
clean:
	rm -f $(TEX_FILES) $(PATCH_FILES) highlight.sty $(UPDATED_FILE)
	rm -f *~