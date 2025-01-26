# Descrition

Rôle de création des branches spécifiques à Access Manager (configuration annuaire AAA agents par défaut)


# Prérequis


# Variables de rôle

```
# Valeur par defaut : annuaire AAA

# Repertoire d'installation de OSDEE
odseeHome: '/var/opt'
# Repertoire odsee dans l'archive oracle (dsee7 par defaut)
odseeDir: 'dsee7'
# Emplacement des binaires d'administration OSDEE
odseeBin: '{{ odseeHome }}/{{ odseeDir }}/bin'
# Emplacement des outils pour Odsee (ldapsearch / ldapmodify etc)
odseeDsrkBin: '{{ odseeHome }}/{{ odseeDir }}/dsrk/bin'

# Emplacement pour la création de l'instance
instanceHome: '/data/ldap'
# Nom de l'instance
instanceName: 'slapd-data-aaa'
# Port
instancePort: '389'
# Port secure (ssl)
instancePortSecure: '636'
# Répertoire de destination des fichiers de password
instancePasswordDir: "/root/ldap"
# Nom du fichier contenant le password de l'instance (utilisé pour toutes les configurations, droits = root 600)
instancePasswordFile: "{{ instanceName }}"

# Organizational Unit (ou) correspondant à l'académie, ex pour Orléans-Tours : ac-orleans-tours
instanceOrganization: 'ac-academie'

# Emplacement de base pour la creation des branches Access Manager
axmSuffix: 'ou={{ instanceOrganization }},ou=education,o=gouv,c=fr'
# Organizational Unit pour les utilisateurs, (+ ctadmin)
axmOu: 'ou=personnels EN'
# dn reconstitué
axmBranch: '{{ axmOu }},{{ axmSuffix }}'
# Administrateur AxM
axmAdmin: 'ctadmin'
# Password du compte ctadmin pour creation dans l'annuaire
axmAdminPassword: 'password@changer!'

```

# Dépendances

Odsee installé (role-ldap-odsee-install)
Instance existante (role-ldap-odsee-instances)
Suffix créés (role-ldap-odsee-suffix)


---

*Auteur*

*Vincent Leblanc <vincent.leblanc2@ac-orleans-tours.fr>*
*Pôle de compétences - gestion des identités - Rectorat d'Orléans-Tours*

*Certaines parties des rôles sont tirées du travail réalisé par JC TOUSSAINT (Nancy) pour l'acv (http://gitlab.tyforge.in.ac-rennes.fr/acv)*
