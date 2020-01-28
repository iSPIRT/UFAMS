pdf: Makefile content/standards.md
	pandoc \
	  -f gfm \
	  --pdf-engine=xelatex \
	  --toc \
	  --number-sections \
	  -V geometry:a4paper \
	  -V geometry:margin=3cm \
	  -V mainfont="Liberation Sans" \
	  -V monofont="Liberation Mono" \
	  --highlight-style components/pygments.theme \
	  -H components/chapter_break.tex \
	  -H components/inline_code.tex \
	  -H components/pdf_properties.tex \
	  -o standards.pdf \
	  content/standards.md

content/standards.md: standards.docx
	pandoc \
	  -f docx \
	  -t gfm  \
	  standards.docx \
	  --output=content/standards.md \
	  --atx-headers \
	  --wrap=none \
	  --toc --extract-media=""

