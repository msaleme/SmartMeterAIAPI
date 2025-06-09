# Smart Meter AI API

An OpenAPI 3.0 specification for AI-powered smart meter data management with Salesforce agent integration.

## Overview

This repository contains a comprehensive OpenAPI specification that defines a RESTful API for managing smart meter data with AI-enhanced capabilities. The API is designed for Salesforce AI agent integration and enables retrieving meter readings, monitoring device status, and handling alerts.

## Features

- **Smart Meter Management**: List and retrieve smart meter information
- **Reading Retrieval**: Access meter readings with date range filtering
- **Alert Monitoring**: Get real-time alerts for meter issues
- **AI Agent Integration**: Built-in Salesforce AI agent topic configuration
- **Status Tracking**: Monitor meter operational states

## API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/meters` | GET | Get list of all registered smart meters |
| `/meters/{meterId}` | GET | Get specific meter details |
| `/meters/{meterId}/readings` | GET | Get meter readings with optional date filtering |
| `/meters/{meterId}/alerts` | GET | Get alerts for a specific meter |

## Data Models

### SmartMeter
- **id**: Unique meter identifier
- **location**: Physical installation location
- **status**: Current status (active, inactive, maintenance)

### MeterReading
- **timestamp**: Reading timestamp (ISO 8601)
- **energyConsumed**: Energy consumption in kWh
- **power**: Current power usage in kW

### MeterAlert
- **timestamp**: Alert timestamp
- **type**: Alert type (overload, outage, tampering, low_voltage)
- **message**: Alert description

## Salesforce AI Agent Configuration

The API includes AI agent topic configuration:

- **Topic**: SmartMeterDataManagement
- **Scope**: Handle smart meter data retrieval and monitoring
- **Key Rules**:
  - Always require meter ID before data retrieval
  - Read-only operations (no data modification)
  - Date range validation for readings
  - Alert troubleshooting guidance

## Usage Examples

```bash
# Get all meters
GET /meters

# Get specific meter
GET /meters/12345

# Get readings for date range
GET /meters/12345/readings?startDate=2024-01-01&endDate=2024-01-31

# Get meter alerts
GET /meters/12345/alerts
```

## Alert Types

- **overload**: Excessive power consumption detected
- **outage**: Power outage condition
- **tampering**: Potential meter tampering
- **low_voltage**: Low voltage condition

## Development

1. **View Specification**: Open `smartmeteraiapi.yaml` in Swagger Editor or similar tool
2. **Generate Code**: Use OpenAPI generators for client/server code
3. **Configure Exchange**: Use `exchange.json` for enterprise asset management

## Tools

- [Swagger Editor](https://editor.swagger.io/)
- [OpenAPI Generator](https://github.com/OpenAPITools/openapi-generator)
- [Postman](https://www.postman.com/)

## Use Cases

- Utility company meter management
- Energy consumption monitoring
- Predictive maintenance with AI
- Customer service automation
- Grid health monitoring