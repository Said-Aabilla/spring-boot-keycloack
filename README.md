# Sample Java Application with Spring Boot 3, Spring Security, and Keycloak

This tutorial explains how to create a sample Java application using Spring Boot 3 and protect it with Spring Security and Keycloak, without requiring Keycloak adapters.

## Prerequisites

- Java 17+
- Docker installed
- Spring Boot 3
- Keycloak 17

---

## Step 1: Install Keycloak

We will install **Keycloak 17** using a Docker container. This will set up an instance of Keycloak where we can manage realms and clients. For this example, we will use `admin` as the username and `password` as the password.

### Commands

```bash
$ docker pull keycloak/keycloak:17.0.0
$ docker run -p 8080:8080 \ 
    -e KEYCLOAK_ADMIN=admin \ 
    -e KEYCLOAK_ADMIN_PASSWORD=password \ 
    keycloak/keycloak:17.0.0 start-dev
```


## Step 2: Create a Realm

After logging in, we will create a new realm. A realm in Keycloak is a space where you define clients, roles, and users.

1. Go to the **Realm settings**.
2. Click on **Add Realm**.
3. Name the realm **external**.

---

## Step 3: Create a Keycloak Client

A client is an application that interacts with Keycloak to authenticate users. We will now create a client with the name **external-client**.

1. Navigate to **Clients** under the newly created realm.
2. Click **Create**.
3. Set the following configurations:

   - **Client ID**: `external-client`
   - **Enabled**: On
   - **Client Protocol**: `openid-connect`
   - **Access Type**: `Confidential`
   - **Standard Flow Enabled**: On
   - **Direct Access Grants Enabled**: On
   - **Valid Redirect URIs**: `http://localhost:8081/*`

4. Save the changes.

---

## Step 4: Create a User

Now we will create a user for our **external** realm. This user will be used to authenticate with the Java application.

1. Navigate to **Users**.
2. Click **Add User**.
3. Set

## Step 5: Change your application.properties to include your secret client, then you are ready to run the app.

