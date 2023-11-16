# Spring Security

## Use Multiple SecurityFilterChains

```java
    @Bean
	@Order(1)                                                        
	public SecurityFilterChain apiFilterChain(HttpSecurity http) throws Exception {
		http
			.securityMatcher("/api/**")                                   
			.authorizeHttpRequests(authorize -> authorize
				.anyRequest().hasRole("ADMIN")
			)
			.httpBasic(withDefaults());
		return http.build();
	}

	@Bean                                                            
	public SecurityFilterChain formLoginFilterChain(HttpSecurity http) throws Exception {
		http
			.authorizeHttpRequests(authorize -> authorize
				.anyRequest().authenticated()
			)
			.formLogin(withDefaults());
		return http.build();
	}
```

The SecurityFilterChain which is no @Order will defaults to last to attempt to match routing.