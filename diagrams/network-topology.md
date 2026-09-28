# Network Topology

## Laboratory Topology

```text
                    HOST COMPUTER
                         │
                      Hyper-V
                         │
                    ┌────▼────┐
                    │ LAB-AD  │
                    │ Network │
                    └────┬────┘
                         │
              ┌──────────┴────────────┐
              │                       │
        ┌─────▼──────┐          ┌──────▼─────┐
        │    DC01    │          │  CLIENT01  │
        │            │          │            │
        │ Win Server │          │ Windows 11 │
        │ AD DS      │ ◄──────► │ Domain     │
        │ DNS        │          │ Client     │
        └────────────┘          └────────────┘
        192.168.100.10
```

## Network

```text
Network: 192.168.100.0/24
DC01:    192.168.100.10
```

The network is isolated through an internal Hyper-V virtual switch.
