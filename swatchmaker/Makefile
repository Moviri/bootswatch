#
# BUILD BOOTSWATCH SWATCH
#

OUTPUT_PATH = swatch

bootswatch:
	recess --compile swatchmaker.less > ${OUTPUT_PATH}/bootstrap.css
	recess --compress swatchmaker.less > ${OUTPUT_PATH}/bootstrap.min.css
	recess --compile swatchmaker-responsive.less > ${OUTPUT_PATH}/bootstrap-responsive.css
	recess --compress swatchmaker-responsive.less > ${OUTPUT_PATH}/bootstrap-responsive.min.css

bootmoda:
	recess --compile  modamaker.less > moda/bootstrap.css
	recess --compress  modamaker.less > moda/bootstrap.min.css
#	recess --compile modamaker-responsive.less > moda/bootstrap-responsive.css
#	recess --compress  modamaker-responsive.less > moda/bootstrap-responsive.min.css
	recess --compile  modamaker.extensions.less > moda/bootstrap.extensions.css
	recess --compress  modamaker.extensions.less > moda/bootstrap.extensions.min.css

bootcwdemo:
	recess --compile  cwdemomaker.less > cwdemo/bootstrap.css
	recess --compress  cwdemomaker.less > cwdemo/bootstrap.min.css
	recess --compile cwdemomaker-responsive.less > cwdemo/bootstrap-responsive.css
	recess --compress  cwdemomaker-responsive.less > cwdemo/bootstrap-responsive.min.css

bootstrap:
	-test -d bootstrap && rm -r bootstrap
	curl --location -o latest_bootstrap.tar.gz https://github.com/twitter/bootstrap/tarball/master
	tar -xvzf latest_bootstrap.tar.gz
	mv twitter-bootstrap* bootstrap
	rm latest_bootstrap.tar.gz

default:
	-test -f ${OUTPUT_PATH}/variables.less && rm ${OUTPUT_PATH}/variables.less
	-test -f ${OUTPUT_PATH}/bootswatch.less && rm ${OUTPUT_PATH}/bootswatch.less
	curl --location -o ${OUTPUT_PATH}/variables.less https://raw.github.com/twitter/bootstrap/master/less/variables.less
	curl --location -o ${OUTPUT_PATH}/bootswatch.less https://raw.github.com/thomaspark/bootswatch/gh-pages/swatchmaker/swatch/bootswatch.less
	make bootswatch

watcher:
	ruby watcher.rb

server:
	open http://localhost:8000/test/test.html
	python -m SimpleHTTPServer

.PHONY: bootswatch bootstrap default watcher server

