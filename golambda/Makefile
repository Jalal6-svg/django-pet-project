BINARY_NAME=bootstrap
BUILD_DIR=bin


.PHONY: build clean deploy

build:
	@echo "building go binary for lambda.."
	GOOS=linux GOARCH=arm64 go build -tags lambda.norpc -o $(BUILD_DIR)/$(BINARY_NAME) main.go
	@echo "build complete: $(BUILD_DIR)/$(BINARY_NAME)"

zip: build
	@echo "zipping binary.."
	cd $(BUILD_DIR) && zip function.zip $(BINARY_NAME)
	@echo "zip created: $(BUILD_DIR)/function.zip"

clean:
	@echo "cleaning.."
	rm -rf $(BUILD_DIR)