# Pre-built Pentest Tools for Kali ARM64
Various tool binaries compiled for Kali ARM.

## Tools
| Tool | Description | Source Repository |
| :--- | :--- | :--- |
| **Kerbrute** | A tool to perform Kerberos pre-auth bruteforcing (user enumeration, password spraying, AS-REP Roasting). | [ropnop/kerbrute](https://github.com/ropnop/kerbrute) |

## Usage

1. Clone this repository or download the specific binary you need.
2. Make the file executable:
   ```bash
   chmod +x <binary_name>
   ```

## Build Instructions & Troubleshooting (Kali ARM64)

Below are the steps of how these binaries were compiled in a Kali Linux ARM64 environment, including the common errors encountered and their solutions.
**Environment:** Kali Linux ARM64

### Building `Kerbrute`

**Steps:**

1. Install Go version `go1.2x`:
   ```bash
   apt install gccgo-go
   apt install golang-go
   ```

2. If Kali could not resolve external domains: `dial tcp: lookup proxy.golang.org on 172.16.97.2:53: no such host`, configure the system DNS to use Google's public DNS by modifying `/etc/resolv.conf`:
   ```bash
   sudo bash -c 'echo "nameserver 8.8.8.8" > /etc/resolv.conf'
   ```

3. Final Build Process:
   ```bash
   git clone https://github.com/ropnop/kerbrute.git
   cd kerbrute
   sudo make linux
   ```
The compiled binaries will be outputted to the `dist/` directory. For ARM64 environments, use the `kerbrute_linux_arm64` binary.

**References:**
- [ropnop/kerbrute Issue #50](https://github.com/ropnop/kerbrute/issues/50)
