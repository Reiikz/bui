VERSION=0.0.0
FOLDER_NAME=bui-common_$(VERSION)_all

makedeb:
	@rm -rf $(FOLDER_NAME).deb
	@rm -rf $(FOLDER_NAME)
	@mkdir -p $(FOLDER_NAME)
	@cp -R DEBIAN $(FOLDER_NAME)
	@cp -R etc $(FOLDER_NAME)
	@cp -R usr $(FOLDER_NAME)
	@gzip $(FOLDER_NAME)/usr/share/man/man8/bui-cfgh.8
	@chmod -R 700 $(FOLDER_NAME)/etc
	@chmod -R 555 $(FOLDER_NAME)/usr
	@dpkg-deb -b $(FOLDER_NAME)
	@chmod 700 -R $(FOLDER_NAME)
