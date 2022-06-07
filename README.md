# ehttp
![origin makefile project](https://github.com/hongliuliao/ehttp)
![current cmake project](https://github.com/ausk/ehttp)

This library make http (with json) microservice easy!

## Feature
* Base on linux epoll
* Multi-thread model

## Performance (without log print)
 * Connect per request: qps 12000+ ([ab](https://github.com/CloudFundoo/ApacheBench-ab) -c 10 -n 10000 localhost:3456/hello)
 * Connection keep alive: qps 18000+ ([ab](https://github.com/CloudFundoo/ApacheBench-ab) -c 10 -n 10000 -k localhost:3456/hello)

## Build && Test
```
# make && make test && ./output/test/hello_server 3456
 mkdir -p build && cd build && cmake .. && make && ./test/hello_server 3456

 curl "localhost:3456/hello"
 curl -d "name=tom&pwd=3" "localhost:3456/login"
```

## Function List
  * http 1.0/1.1(keep-alive support) GET/POST request
  * response as json format

## Example
```c++
#include <sstream>
#include <cstdlib>
#include "simple_log.h"
#include "http_server.h"

// Make sure the callback method is threadsafe
void login(Request &request, Json::Value &root) {
    std::string name = request.get_param("name");
    std::string pwd = request.get_param("pwd");

    LOG_DEBUG("login user which name:%s, pwd:%s", name.c_str(), pwd.c_str());

    root["code"] = 0;
    root["msg"] = "login success!";
}

int main() {
    HttpServer http_server;

    http_server.add_mapping("/login", login, POST_METHOD);

    http_server.set_port(3456);
    http_server.start_sync();
    return 0;
}
```

## Run
```
ausk@ubuntu:~/projs/ehttp$ curl -d "name=tom&pwd=3" "localhost:3456/login"
{"code":0,"msg":"login success!"}
```

