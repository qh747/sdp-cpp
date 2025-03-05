# sdp++
1. origin link: https://gitee.com/taoweitao/sdp-cpp.git
2. modified file CMakeLists.txt
3. library generated in sdp-cpp/lib
4. binary file generated in sdp-cpp/bin

## Compile

```
1. cmake -B build
2. cmake --build build -j4
```

The library should be then availeble at `lib/libsdp-cpp.a  lib/libabnf.a   lib/libbuilders.a`
The binary file should be then availeble at `bin/Parser`

## Usage 

Just include the `SessionDescription.h`  header from the `include` directory

### Parsing an sdp string
```
#include "SessionDescription.h"

void main()
{
	try {
		auto sdp = sdp::SessionDescription::parse("v=0\r\n"
			"o=- 3803220250780278427 2 IN IP4 127.0.0.1\r\n"
			"s=-\r\n"
			"t=0 0\r\n"
			"a=msid-semantic: WMS\r\n"
			"m=application 50895 DTLS/SCTP 5000\r\n"
			"a=crypto:1 AES_CM_128_HMAC_SHA1_80 inline:CoKH4lo5t34SYU0pqeJGwes2gJCEWKFmLUv/q0sN|2^48\r\n"
			"a=sctpmap:5000 webrtc-datachannel 1024\r\n");
	} catch (const std::exception& e) { 
		std::cout << e.what();
	}
}
```

### Createing and serializing an sdp object
```
#include "SessionDescription.h"

void main()
{
	sdp::SessionDescription sdp;
	auto origin = std::make_shared<sdp::Origin>("-", 0, 0, "IN", "IP4", "127.0.0.1");
	sdp.setOrigin(origin);
	sdp.setSessionName("test");
	auto audio = std::make_shared<sdp::MediaDescription>("audio", 9, "UDP/AVP");
	sdp.addMedia(audio);

	std::cout << sdp.toString();
}
```

## License
MIT

