FROM nginx:1.17.4

# copy project from base server image
COPY --from={{ base_server_path }} /home/app/ /home/app/
COPY --from={{ base_server_path }} /home/site/ /home/site/
COPY --from={{ base_server_path }} /home/panel/ /home/panel/

# nginx configs
RUN rm /etc/nginx/conf.d/default.conf
RUN ln -s /home/app/deployment/{{ deployment_path }}/doc/passwd /etc/nginx/.htpasswd && \
    ln -s /home/app/deployment/{{ deployment_path }}/doc/nginx.conf /etc/nginx/conf.d/doc.conf
RUN ln -s /home/app/deployment/{{ deployment_path }}/app/nginx.conf /etc/nginx/conf.d/app.conf
RUN ln -s /home/site/deployment/{{ deployment_path }}/nginx.conf /etc/nginx/conf.d/site.conf && \
    ln -s /home/panel/deployment/{{ deployment_path }}/nginx.conf /etc/nginx/conf.d/panel.conf