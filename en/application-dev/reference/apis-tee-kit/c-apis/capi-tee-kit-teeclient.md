# TeeClient

## Overview

Provides APIs for the client applications (CAs) in the Rich Execution Environment (normal mode) to access the trusted applications (TAs) in a Trusted Execution Environment (TEE).

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

## Files

| Name | Description |
| -- | -- |
| [tee_client_api.h](capi-tee-client-api-h.md) | Defines APIs for CAs to access TAs.<br> <p> Example: <p>1. Initialize a TEE: Call <b>TEEC_InitializeContext</b> to initialize the TEE. <p>2. Open a session: Call <b>TEEC_OpenSession</b> with the Universal Unique Identifier (UUID) of the TA. <p>3. Send a command: Call <b>TEEC_InvokeCommand</b> to send a command to the TA. <p>4. Close the session: Call <b>TEEC_CloseSession</b> to close the session. <p>5. Close the TEE: Call <b>TEEC_FinalizeContext</b> to close the TEE. |
| [tee_client_type.h](capi-tee-client-type-h.md) | Defines basic data types and data structures. |
| [tee_client_constants.h](capi-tee-client-constants-h.md) | Defines public data and constants. |
