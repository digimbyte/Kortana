# Kortana Commons License (KCL-1.1)

## Preamble
This license merges open collaboration with sustainable funding:
- Freedom to inspect, modify, and privately share
- Commercialization requires supporting development
- Shared improvements benefit all

## 1. Definitions
```text
"Project" - Official Kortana repositories & maintainers
"Derivative Work" - Any modified version (fork, patch, etc)
"Commercial Use" - Any revenue-generating activity
"Cloud Services" - Kortana-hosted APIs requiring auth
```

## 2. Permissions
```text
✅ Private use & modification
✅ Academic/research deployment
✅ Distribution to <10 users
✅ Contribution to official Project
✅ Fork maintenance (with §3 conditions)
```

## 3. Conditions
### For Derivatives:
```yaml
branding:
  name: "Must include 'Unofficial' prefix"
  visuals: "≤30% similarity to official branding"
  disclaimers:
    - "Not affiliated with Kortana Project"
    - "community-fork.example.com"

license:
  retain_header: true
  updates:
    - "Submit significant patches upstream"
```

### For Commercial Use:
```text
- Purchase $1000/8yr commercial license
- Display "Licensed through kortana.ai"
- 10% revenue share if using Cloud Services
```

## 4. Copyleft Provisions
```dart
// Copyright (c) Kortana Commons
abstract class LicenseEnforcement {
  /// Patches become available to all licensees
  static void enforceCopyleft(Patch patch) {
    if (patch.quality > MIT) {
      Project.applyPatch(patch);
      Forks.syncPatch(patch);
    }
  }
}
```

## 5. Commercial License Terms
```yaml
fee: 
  base: 1000 USD 
  renewal: 800 USD every 8yrs
  cloud_discount: 30% off if using Kortana Cloud

rights:
  - Use official branding
  - Access Cloud Services
  - Priority security patches

termination:
  - Immediate if reverse-engineering Cloud APIs
  - 30-day cure period for other breaches
```

## 6. Contributor Agreement
By contributing:
```text
- You grant Kortana exclusive rights to your work
- You permit relicensing under future KCL versions
- You warrant code has no export restrictions
```

## 7. Cloud Services
```text
Access requires:
- Valid commercial license
- API keys from official registry
- Compliance with usage quotas

Interfaces:
- Voice auth API: api.kortana.ai/v1/voiceprint
- IoT proxy: mqtt-proxy.kortana.ai:8883
```

## 8. Enforcement
### Technical
```bash
# Built-in license checks
kortana-cli validate-license \
  --key ${KORTANA_LICENSE} \
  --cloud-token ${CLOUD_SECRET}
```

### Legal
- Commercial violators: $250/day until compliance
- Fork non-compliance: Public naming + DMCA
- Arbitration in Singapore (SIAC rules)

---

**Full Text & FAQ**: [kortana.ai/legal](https://kortana.ai/legal)  
**License Purchase**: [kortana.ai/pricing](https://kortana.ai/pricing)