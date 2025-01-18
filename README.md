# Ansible Role: ModSecurity

This Ansible role installs and configures ModSecurity with OWASP Core Rule Set (CRS) for Apache web server. ModSecurity is an open-source web application firewall (WAF) that provides real-time web application monitoring, logging, and access control.

## Requirements

- Apache2 web server installed
- Ansible 2.9 or higher
- Debian/Ubuntu Linux (other distributions may work but are not tested)

## Role Variables

### Main Configuration

```yaml
# Enable/disable ModSecurity
modsecurity_enabled: true

# Set ModSecurity to detection-only mode (no blocking)
modsecurity_detection_only: false

# Audit log parts to be recorded
modsecurity_audit_log_parts: "ABCEFHJKZ"
```

### OWASP CRS Configuration

```yaml
# OWASP CRS version to install
modsecurity_crs_version: "3.3.5"

# Enable/disable OWASP CRS
modsecurity_crs_enabled: true
```

### Path Configuration

The role uses OS-specific paths that are automatically set based on the target system. These can be overridden if needed:

```yaml
modsecurity_conf_path: "{{ _modsecurity_conf_path }}"
modsecurity_recommended_conf: "{{ _modsecurity_recommended_conf }}"
modsecurity_apache_config: "{{ _apache_modsecurity_config }}"
```

## Dependencies

None.

## Example Playbook

```yaml
- hosts: webservers
  roles:
    - role: farisc0de.modsecurity
      vars:
        modsecurity_enabled: true
        modsecurity_detection_only: true  # Set to false in production
        modsecurity_crs_enabled: true
```

## Tags

- `modsecurity`: Configure ModSecurity
- `owasp_crs`: Install and configure OWASP CRS
- `always`: Tasks that should always run

## License

MIT

## Author Information

This role was created by [Faris AL-Otaibi](https://github.com/farisc0de).
