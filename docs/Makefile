default: pdf
.PHONY: default

#THIS_DIR := $(CURDIR)/$(dir $(lastword $(MAKEFILE_LIST)))
THIS_DIR := ./

TARGET_BASE :=README
SRC_DIR :=$(THIS_DIR)
TARGET_SRC :=$(SRC_DIR)/../$(TARGET_BASE).md

BIB :=$(SRC_DIR)/references.bib

TEMPLATE_DIR :=$(THIS_DIR)
TEMPLATE :=template.pandoc

# Default geometry
geometry =margin=1cm

$(TARGET_BASE).%:: $(TARGET_SRC) $(TEMPLATE_DIR)/%.$(TEMPLATE) | $(TEMPLATE_DIR)
	pandoc $(TARGET_SRC) -o $(THIS_DIR)/$@ --template=$(TEMPLATE_DIR)/$*.$(TEMPLATE) --biblio $(BIB) --variable geometry:$(geometry)

# Add rules for different file types like this:
pdf: $(TARGET_BASE).pdf
.PHONY: pdf
tex: $(TARGET_BASE).tex
.PHONY: tex
html: $(TARGET_BASE).html
.PHONY: html


# Meta-rules
#===========
print-%:
	@echo $* = $($*)
.PHONY: print-%

clean%:
	-rm $(TARGET_BASE).$*
.PHONY: clean%
