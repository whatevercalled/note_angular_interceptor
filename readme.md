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
``
do something like cache response or error handling it is very useful for handling http request
although its behavior is like middleware but it is more like error logging or diary or handle data
``
