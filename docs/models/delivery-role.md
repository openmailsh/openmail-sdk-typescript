# DeliveryRole

Inbound only. to if your inbox was the main recipient; cc if you were copied on the email.

## Example Usage

```typescript
import { DeliveryRole } from "@openmail/sdk/models";

let value: DeliveryRole = "to";

// Open enum: unrecognized values are captured as Unrecognized<string>
```

## Values

```typescript
"to" | "cc" | Unrecognized<string>
```