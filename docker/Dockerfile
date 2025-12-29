FROM quay.io/jupyter/datascience-notebook:2025-12-22

# Install Deno Jupyter kernel for the notebook user
RUN curl -fsSL https://deno.land/install.sh | sh
ENV DENO_INSTALL="${HOME}/.deno"
ENV PATH="${DENO_INSTALL}/bin:$PATH"
RUN deno jupyter --install