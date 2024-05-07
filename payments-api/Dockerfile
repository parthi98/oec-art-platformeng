# Step 1 - build
FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /build

COPY . . # copy everything from where the dockerfile is, to current workdir inside the container (sloppy but it works)
RUN dotnet publish -o out # compile the dll's and put them in an "out" directory

# Step 2 - runtime (compiled dll:s)
FROM microsoft/dotnet:2.2-aspnetcore-runtime
WORKDIR /app
COPY --from=build /build/out . # copy your compiled dll's from your BUILD CONTAINER and place them inside your runtime container

EXPOSE 5000/tcp # this is only to document what port is in use
ENTRYPOINT [ "dotnet", "payments-api.dll", "--urls", "http://*:5000"] # the name of your DLL to run