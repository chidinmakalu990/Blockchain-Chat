# SecureChat Pro - Quantum-Safe Blockchain Messaging Platform

## Overview

SecureChat Pro is a decentralized communication protocol built on blockchain infrastructure that provides secure, censorship-resistant messaging with quantum-resistant cryptography. The platform features user management, conversation threading, and immutable message storage, all designed to ensure privacy and security in digital communications.

## Features

### Core Messaging
- **Quantum-Safe Encryption**: Messages can be encrypted using quantum-resistant cryptographic methods
- **Immutable Storage**: All messages are permanently stored on the blockchain
- **Thread Support**: Organize conversations with multi-participant threading
- **Priority Messaging**: Set message priorities (0-10 scale)
- **Message Validation**: Content length and format validation

### User Management
- **User Profiles**: Create and manage user profiles with display names and encryption keys
- **Privacy Controls**: Configurable privacy levels (0-10 scale)
- **Contact Management**: Add trusted contacts with nicknames and trust levels
- **User Blocking**: Block unwanted users with reason tracking
- **Account Status**: Active account management and status tracking

### Conversation Threading
- **Multi-Participant Threads**: Support for up to 10 participants per thread
- **Thread Privacy**: Configurable privacy levels for conversations
- **Access Control**: Creator-managed thread permissions
- **Thread Status**: Active/inactive thread management

### Security & Privacy
- **Authorization Checks**: Comprehensive permission validation
- **Self-Protection**: Users cannot target themselves for blocking/messaging
- **Privacy Levels**: Granular privacy control (0-10 scale)
- **Encryption Support**: Optional quantum-safe encryption for messages

## Technical Specifications

### Platform Limits
- **Maximum Message Length**: 1,000 characters
- **Maximum Display Name**: 50 characters
- **Maximum Nickname**: 50 characters
- **Maximum Encryption Key**: 100 characters
- **Maximum Block Reason**: 100 characters
- **Maximum Thread Participants**: 10 users
- **Trust Level Range**: 0-10
- **Privacy Level Range**: 0-10
- **Message Priority Range**: 0-10

### Error Codes
- `200` - Unauthorized Access
- `201` - Message Not Found
- `202` - Invalid Recipient
- `203` - Message Too Long
- `204` - User Already Blocked
- `205` - User Not Blocked
- `206` - Cannot Target Self
- `207` - Invalid Pagination
- `208` - Invalid Parameters
- `209` - Invalid Thread
- `210` - Trust Level Out of Range
- `211` - Privacy Level Out of Range
- `212` - Platform Disabled
- `213` - Insufficient Permissions
- `214` - Invalid Encryption Key
- `215` - Too Many Participants

## API Reference

### Core Messaging Functions

#### `send-message`
Send a message with optional quantum encryption and thread support.
```clarity
(send-message recipient content quantum-encrypt thread-id priority)
```
- `recipient`: Principal address of the message recipient
- `content`: Message content (max 1000 characters)
- `quantum-encrypt`: Boolean flag for quantum encryption
- `thread-id`: Optional thread ID for conversation threading
- `priority`: Message priority (0-10)

#### `get-message`
Retrieve a specific message by ID.
```clarity
(get-message message-id)
```

#### `get-sent-messages`
Get paginated list of messages sent by a user.
```clarity
(get-sent-messages sender limit offset)
```

#### `get-received-messages`
Get paginated list of messages received by a user.
```clarity
(get-received-messages recipient limit offset)
```

### User Management Functions

#### `create-user-profile`
Create a new user profile with encryption settings.
```clarity
(create-user-profile display-name encryption-key privacy-level)
```

#### `update-user-profile`
Update existing user profile information.
```clarity
(update-user-profile display-name encryption-key privacy-level)
```

#### `block-user`
Block a user with a specified reason.
```clarity
(block-user target reason)
```

#### `unblock-user`
Remove a user from the blocked list.
```clarity
(unblock-user target)
```

#### `add-contact`
Add a user to your trusted contacts.
```clarity
(add-contact contact nickname trust-level)
```

#### `remove-contact`
Remove a user from your contacts.
```clarity
(remove-contact contact)
```

### Threading Functions

#### `create-thread`
Create a new conversation thread.
```clarity
(create-thread participants privacy-level)
```

#### `update-thread-status`
Update thread active status (creator only).
```clarity
(update-thread-status thread-id active)
```

#### `get-thread-messages`
Get paginated messages from a thread.
```clarity
(get-thread-messages thread-id limit offset)
```

### Query Functions

#### `get-user-profile`
Retrieve user profile information.
```clarity
(get-user-profile user)
```

#### `is-user-blocked`
Check if a user is blocked by another user.
```clarity
(is-user-blocked checker target)
```

#### `get-contact-info`
Get contact information for a specific user.
```clarity
(get-contact-info owner contact)
```

#### `get-platform-info`
Get comprehensive platform information.
```clarity
(get-platform-info)
```

#### `get-platform-stats`
Get platform usage statistics.
```clarity
(get-platform-stats)
```

### Administrative Functions

#### `set-platform-status`
Enable or disable the platform (admin only).
```clarity
(set-platform-status active)
```

#### `set-maintenance-mode`
Toggle maintenance mode (admin only).
```clarity
(set-maintenance-mode enabled)
```

#### `emergency-shutdown`
Emergency platform shutdown (admin only).
```clarity
(emergency-shutdown reason)
```

## Security Considerations

1. **Message Privacy**: All messages are stored on-chain and are publicly visible unless encrypted
2. **Quantum Resistance**: The platform supports quantum-safe encryption methods
3. **Access Control**: Comprehensive authorization checks prevent unauthorized actions
4. **User Protection**: Built-in mechanisms prevent self-targeting and harassment
5. **Platform Control**: Administrative functions allow for platform management and emergency controls

## Usage Guidelines

### Getting Started
1. Create a user profile with `create-user-profile`
2. Set up encryption keys for quantum-safe messaging
3. Configure privacy levels according to your needs
4. Add trusted contacts for easier communication

### Best Practices
- Use quantum encryption for sensitive communications
- Set appropriate privacy levels for your profile and threads
- Regularly update your encryption keys
- Use meaningful nicknames for contacts to improve organization
- Block users responsibly with clear reasons

### Thread Management
- Keep thread participants to a reasonable number for better performance
- Set appropriate privacy levels for different conversation types
- Use thread creators' ability to manage thread status effectively

## Development and Deployment

This smart contract is written in Clarity for the Stacks blockchain. To deploy:

1. Ensure you have a Stacks wallet set up
2. Deploy the contract to the Stacks blockchain
3. The deploying address becomes the platform administrator
4. Configure initial platform settings as needed