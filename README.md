# CineSeek - Movie Discovery Application

## API Overview

The MoviesDatabase API provides comprehensive access to movie data including titles, release information, genres, and images. This RESTful API offers powerful filtering capabilities by year, genre, and various sorting options. It supports pagination for efficient data retrieval and includes detailed movie metadata such as plot summaries, cast information, and ratings.

## Version

**API Version:** v1

## Available Endpoints

### GET /titles

Retrieve a list of movies with optional filtering

- Supports filtering by year, genre, list type
- Includes pagination with limit and page parameters
- Allows sorting by various criteria (year, popularity, etc.)

### GET /titles/{id}

Get detailed information about a specific movie

### GET /titles/search/{query}

Search for movies by title or keywords

## Request and Response Format

### Typical Request Structure

```http
GET https://moviesdatabase.p.rapidapi.com/titles?year=2023&limit=12&page=1
Headers:
x-rapidapi-host: moviesdatabase.p.rapidapi.com
x-rapidapi-key: YOUR_API_KEY
```

### Response Structure

```json
{
  "page": 1,
  "next": "/titles?limit=12&page=2",
  "entries": 12,
  "results": [
    {
      "id": "tt1234567",
      "primaryImage": {
        "url": "https://example.com/poster.jpg"
      },
      "titleText": {
        "text": "Movie Title"
      },
      "releaseYear": {
        "year": 2023
      }
    }
  ]
}
```

## Authentication

The API uses API key authentication through RapidAPI:

- **Header Required:** `x-rapidapi-key: YOUR_API_KEY`
- **Host Header:** `x-rapidapi-host: moviesdatabase.p.rapidapi.com`
- API keys are obtained through RapidAPI subscription

## Error Handling

Common error responses:

- **401 Unauthorized:** Invalid or missing API key
- **403 Forbidden:** API quota exceeded or subscription required
- **404 Not Found:** Requested resource doesn't exist
- **429 Too Many Requests:** Rate limit exceeded
- **500 Internal Server Error:** Server-side error

Handle errors by checking response status codes and implementing appropriate fallback mechanisms.

## Usage Limits and Best Practices

### Rate Limits

Varies by subscription tier (typically 100-1000 requests per day for free tier)

### Request Optimization

Use pagination to limit response size (recommended limit: 12-50 items)

### Caching

Implement client-side caching to reduce API calls

### Error Handling

Always include try/catch blocks and loading states

### Environment Variables

Store API keys securely in environment variables

### Server-Side Requests

Make API calls from server-side to protect API keys
