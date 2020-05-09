VERSION=0.0.0
FOLDER_NAME=bui-common_$(VERSION)_all

uninstall:
	rm -rf /etc/bui
	rm -rf /usr/local/bin/bui*
	rm -rf /usr/share/man/man8/bui*

install:
	cp -R etc/bui/ /etc
	chmod 700 /etc/bui -R
	cp usr/local/bin/* /usr/local/bin
	chmod 755 -R /usr/local/bin/bui*
	cp usr/share/man/man8/bui*.8 /usr/share/man/man8
	gzip /usr/share/man/man8/bui*.8
	chmod 744 /usr/share/man/man8/bui*.8

clean:
	@rm -rf $(FOLDER_NAME).deb
	@rm -rf $(FOLDER_NAME)

deb: clean
	@mkdir -p $(FOLDER_NAME)
	@cp -R DEBIAN $(FOLDER_NAME)
	@cp -R etc $(FOLDER_NAME)
	@cp -R usr $(FOLDER_NAME)
	@gzip $(FOLDER_NAME)/usr/share/man/man8/bui*.8
	@chmod -R 744 $(FOLDER_NAME)/etc
	@chmod -R 755 $(FOLDER_NAME)/usr
	@chmod -R 744 $(FOLDER_NAME)/usr/share
	@dpkg-deb -b $(FOLDER_NAME)
	@chmod 777 -R $(FOLDER_NAME)
