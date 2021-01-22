ARG BASE_IMAGE

FROM ${BASE_IMAGE}

WORKDIR c:/tools

ADD https://download.microsoft.com/download/1/2/8/128E2E22-C1B9-44A4-BE2A-5859ED1D4592/rewrite_amd64_en-US.msi rewrite_amd64_en-US.msi
RUN Start-Process msiexec.exe -ArgumentList '/i', 'rewrite_amd64_en-US.msi', '/quiet', '/norestart' -NoNewWindow -Wait