all: papers tech-reports

papers: papers/risk-assessment.pdf papers/deconfliction.pdf papers/remote-id.pdf Bibliography.bib

tech-reports: tech-reports/risk-assessment.pdf tech-reports/deconfliction.pdf tech-reports/remote-id.pdf Bibliography.bib

papers/risk-assessment.pdf: papers/risk-assessment.lyx
	lyx --export pdf2 papers/risk-assessment.lyx

papers/deconfliction.pdf: papers/deconfliction.lyx
	lyx --export pdf2 papers/deconfliction.lyx

papers/remote-id.pdf: papers/remote-id.lyx
	lyx --export pdf2 papers/remote-id.lyx

tech-reports/risk-assessment.pdf: tech-reports/risk-assessment.lyx
	lyx --export pdf2 tech-reports/risk-assessment.lyx

tech-reports/deconfliction.pdf: tech-reports/deconfliction.lyx
	lyx --export pdf2 tech-reports/deconfliction.lyx

tech-reports/remote-id.pdf: tech-reports/remote-id.lyx
	lyx --export pdf2 tech-reports/remote-id.lyx

clean:
	rm papers/*.pdf tech-reports/*.pdf