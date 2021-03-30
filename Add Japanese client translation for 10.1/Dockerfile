ARG BASE_IMAGE

FROM ${BASE_IMAGE}

WORKDIR C:/tools

ADD https://sitecoredev.azureedge.net/~/media/97C24289766A4A6382A14092B35740F6.ashx?date=20210222T215847 translations.zip

RUN powershell -Command Expand-Archive -Path ./translations.zip -DestinationPath c:/inetpub/wwwroot/App_Data