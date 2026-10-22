# Gardener Potager — app Home Assistant

Prototype communautaire non officiel. Consultez le README du dépôt parent avant utilisation.

## Installation locale (Home Assistant OS)
1. Installez l'app **Samba share** ou **Studio Code Server** pour accéder au dossier `/addons`.
2. Copiez le dossier `gardener` dans `/addons/gardener`.
3. Dans **Paramètres → Apps → Boutique**, ouvrez le menu ⋮ puis **Recharger**.
4. L'app « Gardener Potager » devrait apparaître dans les apps locales. Installez-la et démarrez-la.
5. Ouvrez `http://IP_DE_HOME_ASSISTANT:8099`.

## Limites
- Non testé sur matériel réel / Supervisor.
- La construction télécharge la branche `main` amont : les dépendances et le build peuvent changer.
- Ingress n'est pas configuré ; l'accès se fait par le port 8099.
- Ne pas exposer le port sur Internet sans sécurisation.
