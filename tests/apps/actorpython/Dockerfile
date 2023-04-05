#
# Copyright 2021 The Dapr Authors
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

FROM python:3.9-slim-buster@sha256:0ac1e4889c90d3117680b33cbdd397e3d95098b4c6bcff8600035fa5343527ed

WORKDIR /app
COPY . . 

RUN pip install -r requirements.txt

EXPOSE 3000
ENTRYPOINT ["python"]
CMD ["flask_service.py"]
