### **Installation de Webmin sur Fedora**  

Webmin est un puissant outil d’administration système basé sur le web. Il permet de gérer divers aspects d’un serveur Fedora, comme les utilisateurs, les services, les mises à jour et la configuration réseau, via une interface graphique accessible depuis un navigateur.  

---

### **1. Installation des dépendances**  
Avant d’installer Webmin, assurez-vous que certaines dépendances sont présentes sur votre système :  
```bash
sudo dnf install -y perl perl-Net-SSLeay openssl perl-IO-Tty
```

---

### **2. Téléchargement et installation de Webmin**  
Webmin n’est pas disponible dans les dépôts officiels de Fedora, il faut donc le télécharger manuellement.  

#### **Télécharger le paquet RPM de Webmin**  
```bash
wget https://www.webmin.com/download/webmin-current.rpm
```

#### **Installer Webmin avec dnf**  
```bash
sudo dnf install -y webmin-current.rpm
```

---

### **3. Vérification du statut et démarrage de Webmin**  
Après l’installation, le service Webmin doit être démarré et activé :  
```bash
sudo systemctl enable --now webmin
```

Pour vérifier que le service fonctionne :  
```bash
sudo systemctl status webmin
```

---

### **4. Accéder à l’interface Webmin**  
Par défaut, Webmin fonctionne sur le port **10000**. Pour y accéder, ouvrez un navigateur et entrez :  
```
https://<adresse-IP-du-serveur>:10000
```
Exemple :  
```
https://192.168.1.100:10000
```
Si vous installez Webmin sur une machine locale, utilisez :  
```
https://localhost:10000
```
**Note :** Webmin utilise HTTPS, donc il se peut que votre navigateur affiche un avertissement de sécurité. Il suffit d’accepter l’exception pour accéder à l’interface.

---

### **5. Configuration du Pare-feu (Si nécessaire)**  
Si vous utilisez un pare-feu sur Fedora, vous devez autoriser le port 10000 :  
```bash
sudo firewall-cmd --permanent --add-port=10000/tcp
sudo firewall-cmd --reload
```

---

### **6. Modifier l’utilisateur et le mot de passe Webmin**  
Par défaut, l’utilisateur **root** est utilisé pour se connecter à Webmin. Si vous souhaitez définir un mot de passe spécifique pour root :  
```bash
sudo /usr/libexec/webmin/changepass.pl /etc/webmin root NouveauMotDePasse
```

---

### **7. Désinstaller Webmin (Si nécessaire)**  
Si vous souhaitez supprimer Webmin de votre système :  
```bash
sudo dnf remove webmin
sudo rm -rf /etc/webmin
```

---

### **Conclusion**  
Webmin est un excellent outil pour l’administration à distance d’un serveur Fedora. Avec son interface graphique, il facilite la gestion des services Linux sans avoir à utiliser directement la ligne de commande.  

Besoin d’aide pour configurer un module spécifique sur Webmin ? 😊
