# LonWorksForge Pro

## ANSI/CTA-709.1 LonTalk Protocol & SNVT Network Engineering Studio (v1.0.0)

[![Standard: ANSI/CTA-709.1-D](https://img.shields.io/badge/Standard-ANSI%2FCTA--709.1--D-00f2fe.svg)](https://www.cta.tech) [![Guidelines: LonMark v3.4](https://img.shields.io/badge/Guidelines-LonMark_v3.4-10b981.svg)](https://www.lonmark.org) [![Auditor Score: 100%](https://img.shields.io/badge/Normative_Audit-100%25_PASS-10b981.svg)](./documentation/ARCHITECTURE.md) [![Tests: 10/10 Passed](https://img.shields.io/badge/Tests-10%2F10_Passed-10b981.svg)](./test_lonworks.py)

**LonWorksForge Pro** is an engineering simulation, protocol decoder, and channel sizing suite for **LonWorks (ANSI/CTA-709.1 / ISO/IEC 14908\)** building automation networks. It accelerates the engineering, configuration, and diagnostics of peer-to-peer decentralized HVAC, lighting, and industrial building control systems.

---

### Key Capabilities

- **ANSI/CTA-709.1 LonTalk Protocol Codec**: Real-time packet generator and parser supporting Subnet/Node addressing, transport services (ACKD, UNACKD\_RPT, UNACKD, REQUEST), and CCITT CRC-16 checksums (`poly 0x1021`).  
- **Standard Network Variable Type (SNVT) Engine**: Native translation for `SNVT_temp_p` (Temperature), `SNVT_lev_percent` (Position/Level), `SNVT_switch` (Switch & Dimmer), `SNVT_flow` (Flow Rate), `SNVT_press_p` (Pressure), and `SNVT_occupancy` (Occupancy).  
- **Peer-to-Peer Binding Canvas**: 2D interactive topological mapping of masterless input (`nvi`) and output (`nvo`) network variable connections.  
- **FT-10 Physical Channel Sizer**: Verifies cable length rules (up to 500m free topology, 2,700m bus), node transceiver limits (max 64 nodes per channel), and calculates predictive CSMA bandwidth utilization to prevent saturation.  
- **10-Point Normative Protocol Auditor**: Validates packets and channels against 10 critical ANSI/CTA-709.1 and LonMark interoperability rules.  
- **Standalone Python 3 CLI**: Command-line tool (`build/lonworks-cli.py`) for automated CI/CD pipeline verification and batch packet decoding.

---

### Getting Started

#### Web Studio

Open `source-code/index.html` in any web browser. Zero external dependencies or build servers required.

#### Command-Line Tool

\# Encode an SNVT Temperature packet into LonTalk hex

./build/lonworks-cli.py encode \--snvt SNVT\_temp\_p \--val 21.5 \--src 1/15 \--dst 1/22

\# Decode raw LonTalk packet hex stream

./build/lonworks-cli.py decode \--hex "03 01 01 16 01 0F 01 3F 08 66 12 34"

\# Size an FT-10 Free Topology channel

./build/lonworks-cli.py size \--channel FT\_10\_Free\_Topology \--cable 400 \--nodes 32 \--rate 50

\# Run 10-point normative compliance audit

./build/lonworks-cli.py audit

---

### Automated Verification

Run the unit test suite:

python3 test\_lonworks.py \-v

*Result: 10/10 tests passed in 0.36s.*