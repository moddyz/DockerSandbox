# Arguments.
ARG ASWF_PKG_ORG=aswf
ARG VFXPLATFORM_VERSION=2020

# Use c-vfxall as the base image.  (It has the USD installation)
FROM ${ASWF_PKG_ORG}/ci-vfxall:${VFXPLATFORM_VERSION} as ci-vfxall

# Clone and build USDPluginExamples.
ARG USDPLUGINEXAMPLES_ROOT=/usr/local/USDPluginExamples
RUN git clone https://github.com/moddyz/USDPluginExamples.git ${USDPLUGINEXAMPLES_ROOT}
RUN mkdir ${USDPLUGINEXAMPLES_ROOT}/_build
WORKDIR ${USDPLUGINEXAMPLES_ROOT}/_build
RUN cmake -DUSD_ROOT="/usr/local" \
    -DTBB_ROOT="/usr/local" \
    -DBOOST_ROOT="/usr/local" \
    -DUSE_PYTHON_3=ON \
    -DBUILD_TESTING=ON \
    -DCMAKE_INSTALL_PREFIX=_install \
    ..
RUN cmake --build . \
    --verbose \
    --target install
