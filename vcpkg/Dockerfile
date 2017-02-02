FROM msbuild

# git clone https://github.com/Microsoft/vcpkg vcpkg.git
# This repo will need to exist on the host

# Then patch scripts/fetchDependency.ps1 in the repo
# to use Expand-Archive instead of the (broken) Expand-ZIPFile around line 185.
# Finally we can build!

ADD vcpkg.git /code/vcpkg.git
WORKDIR /code/vcpkg.git

SHELL ["powershell", "-ExecutionPolicy", "Bypass", "-Command", "$ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue';"]
RUN New-Item -ItemType Directory -Path downloads
RUN New-Item -ItemType File -Path downloads/AlwaysAllowEverything
RUN scripts\bootstrap.ps1
RUN .\vcpkg integrate install
