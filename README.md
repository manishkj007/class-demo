
private Filter csrfHeaderFilter() {
    return (ServletRequest request, ServletResponse response, FilterChain filterChain) -> {
        HttpServletResponse httpResponse = (HttpServletResponse) response;
        CsrfToken csrf = (CsrfToken) request.getAttribute(CsrfToken.class.getName());

        if (csrf != null) {
            Cookie cookie = new Cookie("XSRF-TOKEN", csrf.getToken());
            cookie.setPath("/");
            cookie.setHttpOnly(false);
            httpResponse.addCookie(cookie);
        }

        filterChain.doFilter(request, response);
    };
}
