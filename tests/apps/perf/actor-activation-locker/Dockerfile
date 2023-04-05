#
# Copyright 2022 The Dapr Authors
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#     http://www.apache.org/licenses/LICENSE-2.0
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

FROM golang:1.20@sha256:23050c2510e0a920d66b48afdc40043bcfe2e25d044a2d7b33475632d83ab6c7 as build_env

ENV CGO_ENABLED=0
WORKDIR /app
COPY . .
RUN go get -d -v
RUN go build -o app .

FROM gcr.io/distroless/static:nonroot@sha256:149531e38c7e4554d4a6725d7d70593ef9f9881358809463800669ac89f3b0ec
WORKDIR /
COPY --from=build_env /app/app /
CMD ["/app"]
