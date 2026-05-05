#  Web Security Scanner (Python)

[![Python Version](https://img.shields.io/badge/python-3.6%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Educational](https://img.shields.io/badge/purpose-educational-green.svg)](https://github.com)

A Python-based VAPT (Vulnerability Assessment and Penetration Testing) tool developed by me to identify common web security vulnerabilities like SQL Injection, XSS, and misconfigured security headers.
This project was customized and enhanced by me for learning and interview preparation purposes.
TEST CHANGE FOR GIT CHECK

 
## 🎯 Features
- OWASP Top 10 vulnerability detection
- SQL Injection detection
- Cross-Site Scripting (XSS) detection
- Directory Traversal detection
- Security Headers analysis
- Information Disclosure detection
- Multi-threaded scanning
- JSON reporting
- Custom Risk Score calculation
- Improved output formatting
- Optimized crawling with URL limits
## 🛠️ Installation

### Prerequisites
- Python 3.6 or higher
- pip package manager

### Setup
1. Clone the repository:
```bash
git clone https://github.com/manjeet-ai-git/python-vapt-security-tool.git
cd simple-web-vuln-scanner
```

2. Install required dependencies:
```bash
pip install -r requirements.txt
```

### Dependencies
Create a `requirements.txt` file with:
```
requests>=2.25.1
beautifulsoup4>=4.9.3
lxml>=4.6.3
```

## 🚀 Usage

### Basic Usage
```bash
python kripsarsi.py http://example.com
```

### Advanced Options
```bash
python kripsarsi.py http://example.com --timeout 15 --threads 10 --output report.json
```
## ⚙️ How It Works
1. Accepts target URL from CLI input  
2. Normalizes URL (ensures valid HTTP/HTTPS format)  
3. Performs lightweight crawling to collect internal endpoints  
4. Each endpoint is analyzed using security test modules:
   - SQL Injection detection
   - XSS reflection checks
   - Directory traversal validation
5. Security headers are evaluated for misconfigurations  
6. Findings are classified into severity levels (High / Medium / Low)  
7. Final structured report is generated with risk score logic  
### Command Line Arguments
- `url`: Target URL to scan (required)
- `--timeout`: Request timeout in seconds (default: 10)
- `--threads`: Number of concurrent threads (default: 5)
- `--output`: Save detailed report to JSON file

## 🔍 Vulnerability Detection

### 1. SQL Injection
- Tests common SQL injection payloads
- Detects database error messages
- Checks GET parameters for injection points

### 2. Cross-Site Scripting (XSS)
- Tests reflected XSS vulnerabilities
- Uses various XSS payloads
- Checks for script execution in responses

### 3. Directory Traversal
- Tests path traversal attacks
- Looks for system file access
- Checks multiple encoding variations

### 4. Security Headers
- X-Frame-Options
- X-XSS-Protection
- X-Content-Type-Options
- Strict-Transport-Security
- Content-Security-Policy
- Referrer-Policy

### 5. Information Disclosure
- Sensitive file detection
- Configuration file exposure
- Development artifacts

## ⚠️ Legal Disclaimer

**IMPORTANT**: This tool is for educational and authorized testing purposes only.

- ✅ **DO**: Use on your own websites and applications
- ✅ **DO**: Use in authorized penetration testing engagements
- ✅ **DO**: Use for learning cybersecurity concepts
- ❌ **DON'T**: Use on websites without explicit permission
- ❌ **DON'T**: Use for malicious purposes
- ❌ **DON'T**: Use to attack or harm others' systems

**You are responsible for ensuring you have proper authorization before scanning any target.**

## 🎓 Educational Value

This scanner helps you understand:
- Common web application vulnerabilities
- How security testing tools work
- OWASP Top 10 security risks
- HTTP requests and responses
- Web application security concepts

## 🔧 Customization

### Adding New Vulnerability Checks
1. Create a new method in the `VulnerabilityScanner` class
2. Follow the naming convention: `check_vulnerability_name()`
3. Use `self.log_vulnerability()` to report findings
4. Add the check to the `scan_target()` method

### Example: Adding a new check
```python
def check_weak_passwords(self, url):
    common_passwords = ['admin', 'password', '123456']
    
    for password in common_passwords:
        response = self.safe_request(url, method='POST', 
                                   data={'username': 'admin', 'password': password})
        
        if response and 'welcome' in response.text.lower():
            self.log_vulnerability(
                "Weak Authentication",
                url,
                f"Weak password accepted: {password}",
                "High"
            )
```

## 📊 Report Formats

### Console Output
- Real-time vulnerability detection
- Color-coded severity levels
- Summary statistics

### JSON Report
```json
{
  "type": "SQL Injection",
  "url": "https://xxxx.com/login?id=1",
  "description": "Possible SQL injection in parameter 'id'",
  "severity": "High",
  "timestamp": "2025-07-27 00:30:25"
}
```

## 🤝 Contributing

We welcome contributions! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Ideas for Contributions
- Add new vulnerability checks
- Improve detection accuracy
- Add support for authentication
- Create GUI interface
- Add more report formats
- Improve documentation

## 📚 Learning Resources

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [Web Application Security Testing](https://owasp.org/www-project-web-security-testing-guide/)
- [Python Security](https://python-security.readthedocs.io/)
- [Ethical Hacking Resources](https://www.cybrary.it/)

## 📝 Changelog

### v1.0.1 (2025-07-27)
- Initial release
- SQL injection detection
- XSS vulnerability testing
- Directory traversal checks
- Security headers analysis
- Information disclosure detection
- Multi-threaded scanning
- JSON report generation

## 🐛 Known Issues

- Limited to basic vulnerability detection
- May produce false positives
- Requires manual verification of results
- No authentication support yet

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- OWASP community for security guidelines
- Security research community
- Python security libraries contributors

## 📞 Support

If you have questions or need help:
- Open an issue on GitHub
- Check the documentation
- Review the code comments

---
## 🚀 Project Goal

The goal of this project was to understand how basic vulnerability scanners work and implement core VAPT concepts in a simple and beginner-friendly way.

## 🚀 Future Improvements

- Authentication-based scanning module
- GUI dashboard for visualization
- API-based scanning support
- Export reports in HTML format

## 👨‍💻 My Contribution

- Modified and enhanced the original scanner
- Added risk scoring system to evaluate vulnerabilities
- Improved output formatting for better understanding
- Optimized crawling and scanning logic
- Customized project for beginner-level understanding and interview explanation

**Remember**: With great power comes great responsibility. Use this tool ethically and legally!


