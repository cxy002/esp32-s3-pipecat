set(COMMON_SRC "main.cpp" "deepmem_ws.cpp")

if(IDF_TARGET STREQUAL linux)
	idf_component_register(
		SRCS ${COMMON_SRC}
		REQUIRES esp-tls tcp_transport)
else()
	idf_component_register(
		SRCS ${COMMON_SRC} "wifi.cpp" "screen.cpp"
		REQUIRES driver esp_wifi nvs_flash esp_psram esp-tls tcp_transport mbedtls lvgl)
endif()
