# RSS Aggregator Webhook - n8n Workflow

Workflow n8n do agregowania, filtrowania i formatowania wiadomości z wielu kanałów RSS z możliwością zwracania wyników przez webhook API.

## 🚀 Funkcjonalności

- **Agregacja wieloźródłowa** - pobieranie artykułów z wielu feedów RSS zapisanych w Data Table
- **Deduplikacja** - automatyczne usuwanie duplikatów na podstawie linków
- **Filtrowanie i sortowanie** - po dacie, tytule lub kategorii
- **Wzbogacanie danych** - dodawanie metadanych, ekstrakcja obrazów, generowanie podsumowań
- **Webhook API** - zwracanie sformatowanych danych przez endpoint HTTP
- **Statystyki** - liczba artykułów, źródła, kategorie, zakres dat

## 📋 Wymagania

- n8n (self-hosted lub cloud)
- Data Table z kolumną `url` zawierającą adresy feedów RSS
- Opcjonalne kolumny: `name`, `category`, `language`

## 🔧 Instalacja

1. Zaimportuj workflow do n8n
2. Skonfiguruj Data Table z i podmień jej ID w scenariuszu.
3. Dodaj źródła RSS do tabeli
4. Aktywuj workflow
5. Skopiuj URL webhooka z node'a "Webhook Trigger"

## 🌐 Użycie API

### Endpoint
```
GET /webhook/rss-aggregator
```

### Parametry Query (opcjonalne)

| Parametr | Typ | Domyślnie | Opis |
|----------|-----|-----------|------|
| `limit` | integer | 50 | Maksymalna liczba zwracanych artykułów |
| `sortBy` | string | date | Sortowanie: `date` lub `title` |
| `category` | string | - | Filtrowanie po kategorii |

### Przykłady
```bash
# Podstawowe wywołanie
curl https://your-n8n.com/webhook/rss-aggregator

# Z parametrami
curl "https://your-n8n.com/webhook/rss-aggregator?limit=10&sortBy=date&category=tech"
```

### Przykładowa odpowiedź
```json
{
  "success": true,
  "timestamp": "2026-01-19T10:30:00.000Z",
  "stats": {
    "totalArticles": 10,
    "totalFetched": 150,
    "sources": 5,
    "categories": ["tech", "AI", "programming"],
    "dateRange": {
      "oldest": "2026-01-18T08:00:00.000Z",
      "newest": "2026-01-19T10:00:00.000Z"
    }
  },
  "articles": [
    {
      "title": "Example Article",
      "link": "https://example.com/article",
      "description": "Article description...",
      "summary": "First 200 characters...",
      "pubDate": "2026-01-19T09:00:00.000Z",
      "creator": "John Doe",
      "categories": ["tech"],
      "imageUrl": "https://example.com/image.jpg",
      "source": {
        "name": "Tech Blog",
        "url": "https://techblog.com"
      }
    }
  ]
}
```

## 🏗️ Struktura Workflow
```
Webhook Trigger → Get RSS Sources → Loop Over Sources → Read RSS Feed 
                                          ↓                    ↓
                                   Aggregate Point ← Enrich RSS Items
                                          ↓
                              Remove Duplicates
                                          ↓
                              Format & Enrich Data
                                          ↓
                                Return Response
```

## ⚙️ Konfiguracja Data Table

Zalecane kolumny w tabeli źródeł RSS:

| Kolumna | Typ | Wymagane | Opis |
|---------|-----|----------|------|
| `url` | string | ✅ | Adres URL feeda RSS |
| `name` | string | ❌ | Nazwa źródła |
| `category` | string | ❌ | Kategoria (np. tech, news, sport) |
| `language` | string | ❌ | Język (np. pl, en) |

## 🔒 Bezpieczeństwo

- Rozważ dodanie autentykacji do webhooka (Header Auth)
- Ogranicz rate limiting w n8n
- Waliduj parametry wejściowe
- Rozważ cache'owanie wyników dla częstych zapytań