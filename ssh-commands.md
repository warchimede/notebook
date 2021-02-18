# Useful ssh commands

### Obtenir la fingerprint d'une clef ssh

```bash
ssh-keygen -E md5 -lf "/path/to/ssh/key" | awk '{ print $2 }' | cut -c 5-;
```

### Lister les identités ssh chargées dans l'agent

```bash
ssh-add -l
```

### Ajouter une identité ssh à l'agent

```bash
ssh-add <path/to/ssh_key>
```