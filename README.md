# ByteCrypt Cache Server

A lightweight TCP socket server implementing an LRU (Least Recently Used) caching system for key-value pair storage and retrieval. Built with Java, this server provides a simple command-line interface for cache operations.

## Features

- LRU (Least Recently Used) caching mechanism
- TCP socket-based client-server communication
- Fixed cache capacity (default: 3 entries)
- Simple command-line interface
- Thread-safe operations

## Getting Started

### Prerequisites

- Java JDK 17 or higher
- Maven (for building)

### Building the Project

```bash
mvn clean package
```

### Running the Server

```bash
java -jar target/caching-proxy-1.0-SNAPSHOT.jar
```

The server will start on port 4000.

### Connecting to the Server

You can connect to the server using netcat (nc) or telnet:

```bash
nc localhost 4000
# or
telnet localhost 4000
```

## Available Commands

| Command | Description | Example |
|---------|-------------|---------|
| `put <key> <value>` | Store or update a key-value pair | `put name john` |
| `get <key>` | Retrieve a value by key | `get name` |
| `print` | Display all cached entries | `print` |
| `exit` | Close the connection | `exit` |

## Example Usage

```
> put name john
Stored [name] -> [john]

> put age 25
Stored [age] -> [25]

> get name
john

> print
[[name] -> [john], [age] -> [25]]

> exit
Connection closed
```

## Technical Details

- Cache implementation uses `LinkedHashMap` for O(1) access time
- LRU eviction policy automatically removes least recently used entries when capacity is reached
- Server handles multiple clients sequentially
- Input sanitization and command validation included

## Error Handling

The server provides meaningful error messages for:
- Invalid commands
- Missing arguments
- Non-existent keys
- Connection issues

## License

MIT License

## Contributing

Feel free to submit issues and enhancement requests!
