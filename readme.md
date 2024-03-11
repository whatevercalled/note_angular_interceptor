https://angular.io/guide/http-interceptor-use-cases

interceptor register globally
```

export const appConfig: ApplicationConfig = {
  providers: [
    provideRouter(
      routes,
      withViewTransitions({
        onViewTransitionCreated: ({ transition }) => {
          const router = inject(Router);
          const targetUrl = router.getCurrentNavigation()!.finalUrl!;
          // Skip the transition if the only thing
          // changing is the fragment and queryParams
          const config: IsActiveMatchOptions = {
            paths: 'exact',
            matrixParams: 'exact',
            fragment: 'ignored',
            queryParams: 'ignored',
          };

          if (router.isActive(targetUrl, config)) {
            transition.skipTransition();
          }
        },
      })
  ),
    provideHttpClient(withInterceptors([errorHandleInterceptor])),
  ],
};
```
```
    provideHttpClient(withInterceptors([errorHandleInterceptor])),
```
