# Custom Excel Form Plugin - Version Avancée

Un plugin WordPress avancé pour créer des formulaires 100% personnalisables qui exportent les données en Excel/CSV et les envoient par e-mail.

## 🚀 Fonctionnalités principales

✅ **Formulaires 100% personnalisables** - L'administrateur peut créer, modifier et supprimer tous les champs
✅ **Types de champs multiples** - Texte, email, téléphone, nombre, zone de texte, menu déroulant, cases à cocher, boutons radio
✅ **Interface d'administration avancée** - Onglets pour la configuration, gestion des champs, design et aperçu
✅ **Génération dynamique** - Le formulaire s'adapte automatiquement aux champs configurés
✅ **Export Excel/CSV** - Génération automatique avec tous les champs personnalisés
✅ **CSS personnalisable** - L'admin peut ajouter son propre CSS
✅ **Messages personnalisables** - Titre, message de succès, sujet email configurables

## Installation

1. Copier le dossier du plugin dans le répertoire `/wp-content/plugins/` de votre installation WordPress
2. Aller dans l'administration WordPress, section "Extensions"
3. Activer le plugin "Custom Excel Form"
4. Configurer le plugin dans "Réglages" > "Excel Form"

## Configuration

Dans l'administration WordPress :

1. Allez dans **Réglages** > **Excel Form**
2. Configurez :
   - **Adresse Email de Destination** : L'email qui recevra les données du formulaire
   - **Sujet de l'Email** : Le sujet des emails envoyés
   - **Notification Utilisateur** : Cochez pour envoyer un email de confirmation à l'utilisateur

## Utilisation

### Afficher le formulaire

Utilisez le shortcode `[custom_excel_form]` dans vos pages ou articles :

```
[custom_excel_form]
```

Ou avec un titre personnalisé :

```
[custom_excel_form title="Mon Formulaire de Devis"]
```

### Champs du formulaire

Le formulaire contient les champs suivants :

**Informations de contact :**
- Nom (obligatoire)
- Prénom (obligatoire)
- Email (obligatoire)
- Téléphone (obligatoire)

**Informations de service :**
- Service (Expédition de Colis / Expédition de Voiture)
- Expéditeur
- Détail du Colis/Voiture
- Quantité
- Destinataire
- Mode de Transport (Avion / Bateau)
- Référence (générée automatiquement)

## Fonctionnalités

- **Validation côté client et serveur** : Validation en temps réel et sécurisée
- **Protection anti-spam** : Champ honeypot invisible
- **Export Excel** : Génération automatique d'un fichier CSV compatible Excel
- **Email automatique** : Envoi des données par email avec fichier en pièce jointe
- **Notification utilisateur** : Email de confirmation optionnel pour l'utilisateur
- **Responsive** : Interface adaptée aux mobiles et tablettes
- **Sécurisé** : Utilisation des nonces WordPress et validation des données

## Développement

### Structure des fichiers

```
custom-excel-form/
├── admin/
│   └── class-admin.php          # Page d'administration
├── assets/
│   ├── custom-excel-form.css    # Styles CSS
│   └── custom-excel-form.js     # JavaScript/AJAX
├── includes/
│   ├── class-custom-excel-form.php   # Classe principale
│   ├── class-form-handler.php        # Traitement du formulaire
│   └── class-excel-generator.php     # Génération des fichiers Excel
├── vendor/                      # Dépendances Composer
└── custom-excel-form.php       # Fichier principal du plugin
```

### Hooks disponibles

Le plugin fournit plusieurs hooks pour l'extensibilité :

```php
// Ajouter des champs au formulaire
do_action('custom_excel_form_additional_fields');

// Filtrer les données avant validation
apply_filters('custom_excel_form_sanitize_data', $cleaned_data, $raw_data);

// Validation personnalisée
apply_filters('custom_excel_form_validate_data', true, $data);

// Personnaliser le corps de l'email
apply_filters('custom_excel_form_email_body', $message, $data);

// Ajouter des données au fichier CSV
do_action('custom_excel_form_add_csv_data', $file, $data);
```

## Dépannage

### Le plugin ne fonctionne pas

1. **Vérifiez les erreurs PHP** : Consultez les logs d'erreur de votre serveur
2. **Vérifiez les permissions** : Le dossier `wp-content/uploads/` doit être accessible en écriture
3. **Vérifiez jQuery** : Le plugin nécessite jQuery (inclus par défaut dans WordPress)
4. **Vérifiez les emails** : Assurez-vous que votre serveur peut envoyer des emails

### Les emails ne sont pas reçus

1. **Vérifiez la configuration SMTP** de votre serveur
2. **Vérifiez les dossiers spam**
3. **Testez avec un plugin SMTP** comme WP Mail SMTP

### Les fichiers Excel ne se génèrent pas

1. **Vérifiez les permissions** du dossier `wp-content/uploads/`
2. **Vérifiez l'espace disque** disponible
3. **Consultez les logs d'erreur** PHP

## Support

Pour obtenir de l'aide :

1. Vérifiez la documentation ci-dessus
2. Consultez les logs d'erreur WordPress
3. Contactez le développeur

---

**Version :** 1.0  
**Auteur :** matondo tech  
**Compatibilité :** WordPress 5.0+  
**PHP :** 7.4+

