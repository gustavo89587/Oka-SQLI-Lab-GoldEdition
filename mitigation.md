# 🛡 SQL Injection Mitigation Playbook – Gold Edition

## 1. Identificação
- Analisar logs Apache  
- Identificar erros SQL expostos  
- Detectar padrões `' OR`, `--`, `=1`  

---

## 2. Contenção
- Bloquear IP ofensivo  
- Desativar endpoint vulnerável  
- Ativar ModSecurity (WAF)  

---

## 3. Erradicação – Correção da Query

### ❌ Vulnerável
```php
$sql = "SELECT * FROM admin WHERE sername='$sername'";
$stmt = $conn->prepare("SELECT * FROM admin WHERE sername=?");
$stmt->bind_param("s", $sername);
$stmt->execute();

