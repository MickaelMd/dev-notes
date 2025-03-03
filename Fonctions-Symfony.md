## Fonctions et Méthodes Clés en Symfony 6.4

### Contrôleurs (Controllers)

*   `render(string $view, array $parameters = []): Response` – Affiche un template Twig.
*   `redirect(string $url, int $status = 302): RedirectResponse` – Redirige vers une URL spécifique.
*   `redirectToRoute(string $route, array $parameters = [], int $status = 302): RedirectResponse` – Redirige vers une route nommée.
*   `json(mixed $data, int $status = 200, array $headers = [], array $context = []): JsonResponse` – Retourne une réponse JSON.
*   `isGranted(mixed $attributes, mixed $subject = null): bool` – Vérifie si l'utilisateur dispose des droits spécifiés.
*   `denyAccessUnlessGranted(mixed $attributes, mixed $subject = null, string $message = 'Access Denied.')` – Refuse l'accès si l'utilisateur n'a pas les droits requis.
*   `createNotFoundException(string $message = 'Not Found', \Throwable $previous = null): NotFoundHttpException` – Génère une exception 404.
*   `createAccessDeniedException(string $message = 'Access Denied', \Throwable $previous = null): AccessDeniedHttpException` – Génère une exception 403.

### Requêtes et Réponses (Requests and Responses)

*   `$request->get(string $key, mixed $default = null): mixed` – Récupère un paramètre de la requête.
*   `$request->query->get(string $key, mixed $default = null): mixed` – Récupère un paramètre GET.
*   `$request->request->get(string $key, mixed $default = null): mixed` – Récupère un paramètre POST.
*   `$request->attributes->get(string $key, mixed $default = null): mixed` – Récupère un attribut de la requête.
*   `$request->cookies->get(string $key, mixed $default = null): mixed` – Récupère un cookie.
*   `$request->files->get(string $key, mixed $default = null): UploadedFile|array|null` – Récupère un fichier uploadé.
*   `$request->getMethod(): string` – Obtient la méthode HTTP de la requête.
*   `$request->getUri(): string` – Obtient l'URI complète de la requête.
*   `$response->setStatusCode(int $code): self` – Définit le code de statut HTTP de la réponse.
*   `$response->headers->set(string $key, string $value, bool $replace = true)` – Définit un en-tête HTTP.
*   `$response->setContent(string $content): self` – Définit le contenu de la réponse.

### Doctrine (ORM)

*   `$entityManager->persist(object $entity): void` – Prépare une entité pour l'enregistrement.
*   `$entityManager->remove(object $entity): void` – Supprime une entité.
*   `$entityManager->flush(): void` – Exécute les opérations en attente sur la base de données.
*   `$repository->find(mixed $id): ?object` – Trouve une entité par son identifiant.
*   `$repository->findOneBy(array $criteria, array $orderBy = null): ?object` – Trouve une entité selon des critères.
*   `$repository->findAll(): array` – Récupère toutes les entités du type.
*   `$repository->findBy(array $criteria, array $orderBy = null, int $limit = null, int $offset = null): array` – Trouve des entités selon des critères.
*   `$repository->count(array $criteria): int` – Compte le nombre d'entités selon des critères.
*   `$queryBuilder = $repository->createQueryBuilder('alias')` – Crée un QueryBuilder pour des requêtes personnalisées.

### Formulaires (Forms)

*   `$formFactory->create(string $type, mixed $data = null, array $options = []): FormInterface` – Crée un formulaire.
*   `$form->handleRequest(Request $request): void` – Traite la requête et remplit le formulaire.
*   `$form->isSubmitted(): bool` – Vérifie si le formulaire a été soumis.
*   `$form->isValid(): bool` – Vérifie si le formulaire est valide.
*   `$form->getData(): mixed` – Récupère les données du formulaire.
*   `$form->get(string $name): FormInterface` – Récupère un champ spécifique du formulaire.
*   `$form->createView(): FormView` – Génère la vue du formulaire pour le rendu dans Twig.
*   `$form->add(string $child, string|null $type = null, array $options = []): self` – Ajoute un champ au formulaire.
*   `$form->remove(string $name): self` – Supprime un champ du formulaire.
*   `$form->has(string $name): bool` – Vérifie si un champ existe dans le formulaire.

### Console

*   `$command->configure(): void` – Configure la commande (nom, description, options, arguments).
*   `$command->execute(InputInterface $input, OutputInterface $output): int` – Exécute la logique de la commande.
*   `$input->getArgument(string $name): mixed` – Récupère un argument de la commande.
*   `$input->getOption(string $name): mixed` – Récupère une option de la commande.
*   `$output->writeln(string $message, int $options = 0): void` – Affiche un message dans la console.
*   `$output->write(string $message, bool $newline = false, int $options = 0): void` – Écrit sans saut de ligne.
*   `$io->success(string|array $messages): void` – Affiche un message de succès.
*   `$io->error(string|array $messages): void` – Affiche un message d’erreur.

### Serializer

*   `$serializer->serialize(mixed $data, string $format, array $context = [])` – Sérialise des données en JSON, XML, etc.
*   `$serializer->deserialize(string $data, string $type, string $format, array $context = [])` – Désérialise une chaîne en objet PHP.

### Messenger

*   `$messageBus->dispatch(object $message): Envelope` – Envoie un message dans un bus.
*   `$envelope->last(HandledStamp::class)?->getResult()` – Récupère le résultat d’un message traité.

### HTTP Client

*   `$response = $httpClient->request('GET', 'https://api.example.com')` – Envoie une requête GET.
*   `$response->getStatusCode(): int` – Récupère le code HTTP.
*   `$response->getContent(): string` – Récupère le contenu brut.
*   `$response->toArray(): array` – Convertit la réponse en tableau.
*   `$response->getHeaders(): array` – Récupère les headers.

### Sécurité (Security)

*   `$security->getUser(): ?UserInterface` – Récupère l'utilisateur actuellement authentifié.
*   `$security->isGranted(string $attribute, mixed $subject = null): bool` – Vérifie si l'utilisateur a une permission.
*   `$security->denyAccessUnlessGranted(string $attribute, mixed $subject = null, string $message = 'Access Denied.')` – Refuse l'accès si l'utilisateur ne possède pas la permission.
*   `$passwordHasher->hashPassword(UserInterface $user, string $plainPassword): string` – Hash un mot de passe.
*   `$passwordHasher->isPasswordValid(UserInterface $user, string $plainPassword): bool` – Vérifie la validité d'un mot de passe.
*   `$authenticator->authenticateUser(UserInterface $user, AuthenticatorInterface $authenticator, Request $request): void` – Authentifie un utilisateur.

### Événements (Event Dispatcher)

*   `$eventDispatcher->dispatch(object $event, string $eventName = null): object` – Déclenche un événement.
*   `$event->stopPropagation(): void` – Arrête la propagation d'un événement.
*   `$event->isPropagationStopped(): bool` – Vérifie si la propagation d’un événement est stoppée.

### Traduction (Translation)

*   `$translator->trans(string $id, array $parameters = [], string $domain = null, string $locale = null): string` – Traduit une chaîne de texte.
*   `$translator->getLocale(): string` – Obtient la locale active.
*   `$translator->setLocale(string $locale): void` – Définit la locale active.

### Sessions

*   `$session->set(string $name, mixed $value): void` – Définit une valeur en session.
*   `$session->get(string $name, mixed $default = null): mixed` – Récupère une valeur en session.
*   `$session->remove(string $name): void` – Supprime une clé en session.
*   `$session->invalidate(int $lifetime = null): bool` – Invalide la session et en crée une nouvelle.

### Cache

*   `$cache->get(string $key, callable $callback): mixed` – Récupère une valeur mise en cache, ou l'enregistre via `$callback`.
*   `$cache->delete(string $key): bool` – Supprime une entrée du cache.
*   `$cache->clear(): bool` – Vide complètement le cache.

### Fichiers et Uploads

*   `$file->guessExtension(): ?string` – Devine l'extension d'un fichier uploadé.
*   `$file->move(string $directory, string $name = null): File` – Déplace un fichier vers un autre dossier.

### Validator

*   `$validator->validate(mixed $value, Constraint|array $constraints = null, array $groups = null): ConstraintViolationListInterface` – Valide une valeur.
*   `$violations->count(): int` – Récupère le nombre d'erreurs de validation.
*   `$violations->get(int $index): ?ConstraintViolationInterface` – Récupère une violation spécifique.

### Templating (Twig)

*   `{{ path('route_name', {'param': value}) }}` – Génère un URL à partir d’une route Symfony.
*   `{{ asset('images/logo.png') }}` – Génère l’URL d’un asset.
*   `{{ include('template.html.twig', { 'var': value }) }}` – Inclut un autre template.
*   `{% for item in collection %} ... {% endfor %}` – Boucle sur une collection d’éléments.
*   `{% if condition %} ... {% endif %}` – Condition dans un template.

### Profiler & Debug

*   `$debugStack->queries` – Liste toutes les requêtes SQL exécutées.
*   `dump($var)` – Affiche une variable dans le debug toolbar.
*   `dd($var)` – Dump & Die : affiche une variable et arrête l'exécution.

### Événements du Kernel

*   `KernelEvents::REQUEST` – Avant qu'une requête soit traitée.
*   `KernelEvents::CONTROLLER` – Juste avant l'exécution d'un contrôleur.
*   `KernelEvents::RESPONSE` – Avant l'envoi de la réponse au client.
*   `KernelEvents::EXCEPTION` – Lorsqu'une exception est levée.
*   `KernelEvents::TERMINATE` – Après l'envoi de la réponse.

### Paramètres et Services

*   `$parameterBag->get(string $name): mixed` – Récupère une valeur de `parameters.yaml`.
*   `$container->get(string $id): mixed` – Récupère un service depuis le conteneur.
*   `$container->has(string $id): bool` – Vérifie si un service est disponible.
