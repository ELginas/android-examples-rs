FROM alvrme/alpine-android:android-33-jdk17

RUN apk add --no-cache rustup build-base musl-dev
RUN extras ndk
RUN echo 1 | rustup-init
ENV PATH /root/.cargo/bin:$PATH
RUN rustup target add aarch64-linux-android
RUN cargo install cargo-ndk

COPY . .
RUN cargo ndk -t arm64-v8a -o app/src/main/jniLibs/ build
RUN ./gradlew build
