FROM node:20-alpine

# Create app group/user
RUN addgroup app && adduser -S -G app app

# Set working directory
WORKDIR /app

# Copy package files first (for caching layer)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the app
COPY . .

# Change file ownership (optional if running as root)
RUN chown -R app:app .

# Use non-root user
USER app

# Expose React's default port
EXPOSE 3000

# Run the app
CMD ["npm", "start"]
