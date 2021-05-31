cette Api est une  application Spring Boot qui prend en charge l'authentification basée sur les tokens  avec JWT :
    
    Notre application Spring Boot peut être résumée dans le diagramme ci-dessous:
 
 
 ![redmi-SpringSecurity](https://user-images.githubusercontent.com/81759205/117460643-05d32b80-af4d-11eb-9e57-58593f09bb44.png)
 
 Spring Security
- WebSecurityConfigurerAdapterest le nœud de notre implémentation de sécurité. Il fournit des -HttpSecurity  pour configurer cors, csrf, gestion de session, règles pour les ressources protégées. Nous pouvons également étendre et personnaliser la configuration par défaut qui contient les éléments ci-dessous.
- UserDetailsService interface a une méthode pour charger l'utilisateur par nom d' utilisateur et renvoie un  objet   Spring Security UserDetails que peut utiliser pour l'authentification et la validation.
- UserDetails contient les informations nécessaires (telles que: nom d'utilisateur, mot de passe, autorités) pour créer un objet d'authentification.
- UsernamePasswordAuthenticationToken obtient {nom d'utilisateur, mot de passe} de la demande de connexion, AuthenticationManager l'utilisera pour authentifier un compte de connexion.
- AuthenticationManager a un DaoAuthenticationProvider (avec l'aide de UserDetailsService& PasswordEncoder) pour valider UsernamePasswordAuthenticationTokenobjet. En cas de succès, AuthenticationManager renvoie un objet Authentification entièrement rempli (y compris les autorisations accordées).
- OncePerRequestFilter effectue une seule exécution pour chaque requête à notre API. Il fournit une méthode  doFilterInternal() qui nous mettrons en œuvre pour analyser et valider JWT, charger les détails de l'utilisateur (en utilisant UserDetailsService), vérifier l'autorisation (en utilisant UsernamePasswordAuthenticationToken).
- AuthenticationEntryPoint détecte une erreur non autorisée et renvoie un 401 lorsque les clients accèdent aux ressources protégées sans authentification.
Le Repository contient UserRepository& RoleRepository pour travailler avec la base de données, sera importé dans le contrôleur .
Le contrôleur reçoit et gère la demande une fois qu'elle a été filtrée par OncePerRequestFilter.
- AuthController gère les demandes d'inscription / de connexion
- TestController  possède accès à des méthodes de ressources protégées avec des validations basées sur les rôles.









pour plus de formations et de ressources consultez

![aaa](https://user-images.githubusercontent.com/81759205/117449673-87708c80-af40-11eb-8d97-bfbc1ff20057.png)
    
  https://lerif.eu/
