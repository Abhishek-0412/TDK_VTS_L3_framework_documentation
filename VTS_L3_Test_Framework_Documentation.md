# VTS L3 Test Framework Documentation

## Table of Contents
1. [Overview](#overview)
2. [Prerequisites](#prerequisites)
3. [Setup Instructions](#setup-instructions)
4. [Configuration](#configuration)
5. [Available Test Suites](#available-test-suites)
6. [Execution Instructions](#execution-instructions)
7. [Output and Reports](#output-and-reports)
8. [Troubleshooting](#troubleshooting)
9. [Advanced Configuration](#advanced-configuration)

## Overview

The **VTS (Vendor Test Suite) L3 Test Framework** is a comprehensive Python-based testing solution designed for L3-level validation of RDK devices. It automates the execution of hardware abstraction layer interface (HAL-IF) tests across multiple device components including Display, Audio, Video, Host, and Deep Sleep functionality.

### Key Features
- **Automated Test Suite Execution**: Streamlined execution of complex L3 test suites
- **Multiple Component Support**: Tests for dsDisplay, dsAudio, dsVideoDevice, dsVideoPort, dsHost, deepsleep, and rmfaudiocapture
- **Interactive Setup**: Python RAFT framework integration with interactive configuration
- **Comprehensive Reporting**: Automatic generation of log files and Excel reports
- **Stream Management**: Automated download and cleanup of test streams
- **Configuration Validation**: Built-in validation for test configurations

### Architecture
- **Main Executor**: `vts_l3_executor.py` - Primary execution engine
- **Common Configuration**: `vts_common_config.py` - Shared device and platform settings
- **Suite-Specific Configs**: Individual configuration files for each test suite
- **RAFT Integration**: Utilizes RDK Automated Framework for Testing (RAFT)

### HAL-IF Test Repositories
The framework uses specific versions of HAL-IF test repositories. Version information is maintained in the [RDK HPK Documentation](https://github.com/rdkcentral/rdk-hpk-documentation/blob/3.1.0/RELEASE.md).

**Current Repository Versions**:
- **Deep Sleep Manager**: [rdk-halif-test-deepsleep_manager v1.4.3](https://github.com/rdkcentral/rdk-halif-test-deepsleep_manager/tree/1.4.3)
- **Power Manager**: [rdk-halif-test-power_manager v1.5.4](https://github.com/rdkcentral/rdk-halif-test-power_manager/tree/1.5.4)
- **Device Settings**: [rdk-halif-test-device_settings v6.0.1](https://github.com/rdkcentral/rdk-halif-test-device_settings/tree/6.0.1)
- **HDMI CEC**: [rdk-halif-test-hdmi_cec v1.6.1](https://github.com/rdkcentral/rdk-halif-test-hdmi_cec/tree/1.6.1)
- **RMF Audio Capture**: [rdk-halif-test-rmf_audio_capture v1.5.4](https://github.com/rdkcentral/rdk-halif-test-rmf_audio_capture/tree/1.5.4)

**Note**: Repository versions are automatically configured in the suite-specific configuration files. Always refer to the latest [RDK HPK Release Documentation](https://github.com/rdkcentral/rdk-hpk-documentation/blob/3.1.0/RELEASE.md) for version updates.

## Prerequisites

### System Requirements
- **Operating System**: Linux environment (Ubuntu 18.04+ recommended)
- **Python**: Python 3.6 or higher
- **Network Access**: Internet connection for repository cloning and stream downloads
- **SSH Access**: SSH connectivity to target device
- **Git**: For repository operations

### Required Python Packages
The framework automatically installs required dependencies, but ensure you have:
- `pandas` - For Excel report generation
- `pyyaml` - For YAML configuration handling
- `subprocess` - For system command execution

### Hardware Setup
- **Target Device**: RDK STB/TV with SSH access enabled
- **Test Streams**: Access to stream server for downloading test content
- **Network Configuration**: Ensure device and test host are on the same network

## Setup Instructions

### Step 1: Download the Framework
```bash
# Download or clone the VTS L3 framework to your local machine
cd /path/to/your/test/directory
# Extract the VTS_L3 framework files
```

### Step 2: Verify Framework Structure
Ensure your directory contains these files:
```
VTS_L3/
├── vts_l3_executor.py           # Main execution script
├── vts_common_config.py         # Common device configuration
├── vtsconfig_deepsleep.py       # Deep Sleep test configuration
├── vtsconfig_dsAudio.py         # Audio test configuration
├── vtsconfig_dsDisplay.py       # Display test configuration
├── vtsconfig_dsHost.py          # Host test configuration
├── vtsconfig_dsVideoDevice.py   # Video Device test configuration
├── vtsconfig_dsVideoPort.py     # Video Port test configuration
└── vtsconfig_rmfaudiocapture.py # RMF Audio Capture test configuration
```

### Step 3: Make Scripts Executable
```bash
chmod +x vts_l3_executor.py
```

## Configuration

### Common Configuration (`vts_common_config.py`)

**CRITICAL**: Update these parameters before running any tests:

```python
# ============= DEVICE CONFIGURATION =============
# Update device IP address
DEVICE_IP = "<YOUR_DEVICE_IP>"  # Replace with your device IP (e.g., "192.168.1.100")

# Update device platform (IMPORTANT: Must match your device)
DEVICE_PLATFORM = "<YOUR_PLATFORM>"    # Options: "Amlogic", "Realtek", "Broadcom"
CPE_PLATFORM = "<YOUR_PLATFORM>"       # Must match DEVICE_PLATFORM
SOC_VENDOR = "<your_platform>"         # lowercase: "amlogic", "realtek", "broadcom"

# Device access credentials
SSH_USERNAME = "root"           # Default SSH username (update if different)
SSH_PASSWORD = ""               # SSH password (if required)
SSH_PORT = 22                   # SSH port number (default is 22)

# Stream configuration
STREAM_DOWNLOAD_PATH = "<YOUR_STREAM_SERVER_URL>"  # Replace with your stream server URL
```

### Suite-Specific Configuration

Each test suite has its own configuration file. Key parameters to verify:

#### Display Tests (`vtsconfig_dsDisplay.py`)
```python
# Monitor configuration - Update with your monitor details
MONITOR_DETAILS = [
    {"Product": "<YOUR_MONITOR_BRAND>", "manufacturerId": "<MANUFACTURER_ID>", "monitorName": "<MONITOR_NAME>"},
    # Add your monitor specifications here
    # Example: {"Product": "Samsung", "manufacturerId": "SAM", "monitorName": "Samsung_TV"}
]
```

#### Audio Tests (`vtsconfig_dsAudio.py`)
- Contains 26 individual test scripts
- Stream rename mappings for audio files
- Audio profile configurations

#### Video Tests (`vtsconfig_dsVideoDevice.py`, `vtsconfig_dsVideoPort.py`)
- Video format support configurations
- Stream download and rename rules
- Port configuration settings

## Available Test Suites

### 1. Display Tests (`dsDisplay`)
**Purpose**: Tests display subsystem functionality including resolution, format support, and monitor detection.

**Key Test Areas**:
- Monitor detection and EDID parsing
- Resolution and refresh rate support
- Color space and HDR capabilities
- Display port functionality

### 2. Audio Tests (`dsAudio`)
**Purpose**: Comprehensive audio subsystem testing including codecs, processing, and output configurations.

**Test Coverage** (26 tests):
- Audio port status and connection
- MS12 audio processing features
- Dolby Volume and dialogue enhancement
- Audio compression and equalization
- ARC (Audio Return Channel) functionality
- Audio delay and synchronization

### 3. Video Device Tests (`dsVideoDevice`)
**Purpose**: Tests video decoding and processing capabilities.

**Key Test Areas**:
- Video codec support
- Resolution and format handling
- Color space processing
- HDR support validation

### 4. Video Port Tests (`dsVideoPort`)
**Purpose**: Tests video output port configurations and capabilities.

**Key Test Areas**:
- Port enumeration and status
- Resolution and format support
- HDR metadata handling
- Color space conversion

### 5. Host Tests (`dsHost`)
**Purpose**: Tests host system integration and power management.

**Key Test Areas**:
- System boot and initialization
- Power state management
- Host communication interfaces
- System resource management

### 6. Deep Sleep Tests (`deepsleep`)
**Purpose**: Tests power management and wake-up functionality.

**Key Test Areas**:
- Deep sleep state transitions
- Wake-up source configuration
- Power consumption validation
- System resume functionality

### 7. RMF Audio Capture Tests (`rmfaudiocapture`)
**Purpose**: Tests RMF (RDK Media Framework) audio capture functionality.

**Key Test Areas**:
- Audio capture initialization
- Stream capture and processing
- Audio format support
- Capture pipeline validation

## Execution Instructions

### Basic Execution

#### 1. Configuration Validation
Before running tests, validate your configuration:

```bash
# Validate display configuration
python vts_l3_executor.py dsDisplay --validate

# Validate audio configuration  
python vts_l3_executor.py dsAudio --validate

# Validate any suite configuration
python vts_l3_executor.py [SUITE_NAME] --validate
```

#### 2. View Current Configuration
```bash
# View display configuration
python vts_l3_executor.py dsDisplay --config

# View audio configuration
python vts_l3_executor.py dsAudio --config
```

#### 3. Update Configuration Files
```bash
# Update configuration files with current parameters
python vts_l3_executor.py dsDisplay --update-config
```

#### 4. Run Test Suite

**IMPORTANT**: Before running any test suite, you must first update the configuration files, then execute the tests.

```bash
# For Display Tests:
python vts_l3_executor.py dsDisplay --update-config
python vts_l3_executor.py dsDisplay

# For Audio Tests:
python vts_l3_executor.py dsAudio --update-config
python vts_l3_executor.py dsAudio

# For Video Device Tests:
python vts_l3_executor.py dsVideoDevice --update-config
python vts_l3_executor.py dsVideoDevice

# For Video Port Tests:
python vts_l3_executor.py dsVideoPort --update-config
python vts_l3_executor.py dsVideoPort

# For Host Tests:
python vts_l3_executor.py dsHost --update-config
python vts_l3_executor.py dsHost

# For Deep Sleep Tests:
python vts_l3_executor.py deepsleep --update-config
python vts_l3_executor.py deepsleep

# For RMF Audio Capture Tests:
python vts_l3_executor.py rmfaudiocapture --update-config
python vts_l3_executor.py rmfaudiocapture
```

**Note**: The `--update-config` step is mandatory as it applies your configuration changes to the test framework's internal configuration files.

### Execution Flow

When you run a test suite, the framework automatically:

1. **Repository Setup**
   - Clones the appropriate HAL-IF test repository
   - Checks out the specified version/tag
   - Sets up the virtual environment
   - Installs required dependencies

2. **Configuration Update**
   - Updates rack configuration with device details
   - Updates device configuration files
   - Modifies stream and player configurations
   - Applies necessary patches for automated execution

3. **Test Environment Setup**
   - Downloads required test streams (if applicable)
   - Configures test environment variables
   - Sets up logging and reporting infrastructure

4. **Test Execution**
   - Launches RAFT framework in interactive mode
   - Executes test cases according to suite configuration
   - Captures real-time output and logs

5. **Post-Execution Cleanup**
   - Generates Excel reports from test logs
   - Cleans up downloaded streams (optional)
   - Preserves log files for analysis

### Interactive Mode

The framework runs in interactive mode, allowing you to:
- Select specific test cases to run
- Monitor test progress in real-time
- Intervene if manual steps are required
- View intermediate results

## Output and Reports

### Log Files
- **Location**: Current directory
- **Format**: `[SUITE]_[TIMESTAMP].log`
- **Content**: Complete test execution log with ANSI escape sequences removed
- **Example**: `dsDisplay_YYYYMMDD_HHMMSS_microseconds.log`

### Excel Reports
- **Location**: Current directory
- **Format**: `[SUITE]_[TIMESTAMP].xlsx`
- **Content**: Structured test results with pass/fail status, execution times, and error details
- **Example**: `dsDisplay_YYYYMMDD_HHMMSS_microseconds.xlsx`

### Report Structure
Excel reports contain:
- **Test Summary**: Overall pass/fail statistics
- **Individual Test Results**: Detailed results for each test case
- **Execution Timeline**: Test execution duration and timestamps
- **Error Details**: Failure reasons and diagnostic information
- **System Information**: Device and environment details

## Troubleshooting

### Common Issues and Solutions

#### 1. SSH Connection Issues
**Problem**: Cannot connect to device via SSH
**Solutions**:
- Verify `DEVICE_IP` in `vts_common_config.py`
- Check network connectivity: `ping <YOUR_DEVICE_IP>`
- Verify SSH credentials and port settings
- Ensure SSH service is running on the device

#### 2. Repository Clone Failures
**Problem**: Git clone operations fail
**Solutions**:
- Check internet connectivity
- Verify repository URLs in configuration files
- Ensure Git is installed and configured
- Check for proxy/firewall restrictions

#### 3. Virtual Environment Issues
**Problem**: Virtual environment activation fails
**Solutions**:
- Ensure Python 3.6+ is installed
- Verify pip and virtualenv are available
- Check disk space for environment creation
- Review install.sh script output for specific errors

#### 4. Stream Download Failures
**Problem**: Test streams cannot be downloaded
**Solutions**:
- Verify `STREAM_DOWNLOAD_PATH` URL accessibility
- Check internet connectivity and DNS resolution
- Verify sufficient disk space on target device
- Review stream server certificate validity

#### 5. Test Execution Hangs
**Problem**: Tests appear to hang or become unresponsive
**Solutions**:
- Check device responsiveness via separate SSH session
- Verify test streams are properly accessible
- Review test-specific requirements (monitor connection, audio setup)
- Check for interactive prompts requiring user input

#### 6. Configuration Validation Errors
**Problem**: Configuration validation fails
**Solutions**:
- Update `DEVICE_PLATFORM` to match your device
- Verify all file paths exist and are accessible
- Check YAML syntax in configuration files
- Ensure monitor details are correctly specified (for display tests)

### Debug Mode
For detailed debugging, you can:
1. Review the generated log files for specific error messages
2. Check the cloned repository's documentation for suite-specific requirements
3. Manually verify configuration files in the test directories
4. Run individual test components outside the framework

### Manual Intervention Points
Some tests may require manual intervention:
- **Monitor Connection**: Ensure monitor is connected for display tests
- **Audio Hardware**: Verify audio output devices are properly connected
- **Stream Validation**: Confirm test streams play correctly on the device
- **Interactive Prompts**: Respond to RAFT framework prompts as needed

## Advanced Configuration

### Environment Variables
Override configuration settings using environment variables:
```bash
# Override device IP
export VTS_DEVICE_IP="<YOUR_DEVICE_IP>"

# Override base path
export VTS_BASE_PATH="<YOUR_CUSTOM_PATH>"

# Run with overrides
python vts_l3_executor.py dsDisplay
```

### Custom Stream Configuration
For suites requiring specific streams, modify the stream rename mappings:
```python
# In suite-specific config file
STREAM_RENAME_MAP = {
    "<original_stream_name.ext>": "<desired_stream_name.ext>",
    "<original_audio.ext>": "<custom_audio_name.ext>"
}
```

### Test Execution Control
Control test execution behavior:
```python
# Stop on first failure
STOP_ON_FAILURE = True

# Continue all tests regardless of failures  
STOP_ON_FAILURE = False
```

### Performance Tuning
Adjust performance parameters:
```python
# Terminal buffer size
TERMINAL_BUFFER_SIZE = 1024

# Select timeout for interactive mode
SELECT_TIMEOUT = 0.1
```

### Custom Test Selection
For audio tests, you can modify the test script list:
```python
TEST_SCRIPT = [
    "dsAudio_test01_EnableDisableAndVerifyAudioPortStatus.py",
    # Add or remove specific test scripts as needed
]
```

---

## Support and Additional Resources

### Documentation References
- **RDK Central**: https://wiki.rdkcentral.com/
- **RDK HPK Documentation**: https://github.com/rdkcentral/rdk-hpk-documentation/blob/3.1.0/RELEASE.md
- **HAL-IF Test Repositories**: Individual repository documentation
- **RAFT Framework**: RDK Automated Framework for Testing documentation

### Version Management
- **HPK Versions**: All HAL component versions are tracked in the [RDK HPK Release Documentation](https://github.com/rdkcentral/rdk-hpk-documentation/blob/3.1.0/RELEASE.md)
- **Repository Pattern**: All test repositories follow the pattern: `https://github.com/rdkcentral/rdk-halif-test-<component>/tree/<version>`
- **Version Updates**: Check the HPK documentation for latest supported versions before updating configuration files

### Best Practices
1. **Always validate configuration** before running tests
2. **Monitor device status** during test execution
3. **Review log files** for detailed error analysis
4. **Backup configurations** before making changes
5. **Test network connectivity** before starting long test suites

### Version Compatibility
- Ensure HAL-IF test repository versions match your device firmware
- Update checkout versions in configuration files as needed
- Verify stream compatibility with your device capabilities

---

*This documentation covers VTS L3 Test Framework version for RDK devices. For the most current information, refer to the individual test repository documentation and RDK Central resources.*