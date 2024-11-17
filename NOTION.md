1. Why did we use Uvicorn to serve up FastAPI rather than a development server?

Unlike Django or Flask, FastAPI does not have a built-in development server. This is both a positive and a negative in my opinion. On the one hand, it does take a bit more to serve up the app in development mode. On the other hand, this helps to conceptually separate the web framework from the web server, which is often a source of confusion for beginners when one moves from development to production with a web framework that does have a built-in development server.

New to ASGI? Read through the excellent Introduction to ASGI: Emergence of an Async Python Web Ecosystem blog post.

2. Configuration
We defined a Settings class with two attributes:

environment - defines the environment (e.g., dev, stage, prod)
testing - defines whether or not we're in test mode

`BaseSettings`, from `pydantic-settings`, validates the data so that when we create an instance of Settings, environment and testing will have types of str and bool, respectively.

`BaseSettings` also automatically reads from environment variables for these config settings. In other words, environment: str = "dev" is equivalent to environment: str = os.getenv("ENVIRONMENT", "dev").
