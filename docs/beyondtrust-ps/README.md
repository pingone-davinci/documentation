# BeyondTrust - Password Safe Connector

Author: Ryan Schafer


# Introduction

Password Safe combines Privileged Account and Session Management (PASM) + Secrets Management capabilities, in one solution. Protect human and machine privileged identities, and your network, against account hijacking, credential re-use attacks, exposed hardcoded passwords, lateral movement, privilege escalation attacks, and more.

# Setup


## Requirements

To use the connector, you'll need:

* API account in Password Safe
* Hostname, API Key and API User
* PingOne tenant


## Setting up the connector

In DaVinci, add a BeyondTrust - Password Safe connection.

Navigate to the “Connectors” tab within DaVinci > search in the top right corner “BeyondTrust - Password Safe” > Click into tile > Click “Add”.

Once the connector is added to the library, you can click into it and configure the General configuration. The connector can then be used as part of a flow.


### Connector settings

The connector has three required fields:
1. Password Safe Hostname: Domain of your Password Safe Environment
2. API Key: API Key from your Password Safe Environment
3. API User: API User of your Password Safe Environment
# Using the connector in a flow
You can use the connector in a variety of use cases, such as:


## Terminate Active Request by Username

Terminates all active requests by Username.

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "username": {
            "type": "string",
            "description": "Username for which you would like to terminate all open requests"
          },
          "reason": {
            "type": "string",
            "description": "A reason or comment why the requests are being changed"
          }
        },
        "required": [
          "username"
        ]
      }
    },
    "example": {
      "properties": {
        "username": "test.admin-adm",
        "reason": "Cancelled because of test"
      }
    }
  }
}

```

Output Schema:
```
{
  "output": {
    "type": "object",
    "properties": {
      "rawResponse": {
        "type": "object"
      },
      "statusCode": {
        "type": "number"
      },
      "headers": {
        "type": "object"
      }
    }
  }
}
```

## Terminate Active Request by Hostname

Terminates all active requests by Hostname

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "hostname": {
            "type": "string",
            "description": "Name of the machine for which you would like to terminate the request"
          },
          "reason": {
            "type": "string",
            "description": "A reason or comment why the requests are being changed"
          }
        },
        "required": [
          "hostname"
        ]
      }
    },
    "example": {
      "properties": {
        "hostname": "LabApp.test.net",
        "reason": "Cancelled because of test"
      }
    }
  }
}
```

Output Schema

```
{
  "output": {
    "type": "object",
    "properties": {
      "rawResponse": {
        "type": "object"
      },
      "statusCode": {
        "type": "number"
      },
      "headers": {
        "type": "object"
      }
    }
  }
}
```

## Terminate Session by Username

Terminates all active sessions by Username

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "username": {
            "type": "string",
            "description": "Username for which you would like to terminate all open sessions"
          }
        },
        "required": [
          "username"
        ]
      }
    },
    "example": {
      "properties": {
        "username": "test.admin-adm"
      }
    }
  }
}
```

Output Schema:

```
{
  "output": {
    "type": "object",
    "properties": {
      "rawResponse": {
        "type": "object"
      },
      "statusCode": {
        "type": "number"
      },
      "headers": {
        "type": "object"
      }
    }
  }
}
```

## Terminate Session by Hostname

Terminates all active sessions by Hostname

Input Schema

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "hostname": {
            "type": "string",
            "description": "Name of the machine for which you would like to terminate the session"
          }
        },
        "required": [
          "hostname"
        ]
      }
    },
    "example": {
      "properties": {
        "hostname": "labApp.test.net"
      }
    }
  }
}
```

Output Schema:

```
{
  "output": {
    "type": "object",
    "properties": {
      "rawResponse": {
        "type": "object"
      },
      "statusCode": {
        "type": "number"
      },
      "headers": {
        "type": "object"
      }
    }
  }
}
```

## Lock Session by Username

Locks all active sessions by Username

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "username": {
            "type": "string",
            "description": "Username for which you would like to lock all open requests"
          }
        },
        "required": [
          "username"
        ]
      }
    },
    "example": {
      "properties": {
        "username": "test.admin-adm"
      }
    }
  }
}
```

Output Schema:

```
{
  "output": {
    "type": "object",
    "properties": {
      "rawResponse": {
        "type": "object"
      },
      "statusCode": {
        "type": "number"
      },
      "headers": {
        "type": "object"
      }
    }
  }
}
```

## Lock Session by Hostname

Locks all active sessions by Hostname

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "hostname": {
            "type": "string",
            "description": "Name of the machine for which you would like to lock the session"
          }
        },
        "required": [
          "hostname"
        ]
      }
    },
    "example": {
      "properties": {
        "hostname": "LabApp1.test.net"
      }
    }
  }
}
```

Output Schema
```
{
  "output": {
    "type": "object",
    "properties": {
      "rawResponse": {
        "type": "object"
      },
      "statusCode": {
        "type": "number"
      },
      "headers": {
        "type": "object"
      }
    }
  }
}
```

## Deny Pending Request by Username

Denies/Cancels an active or pending request

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "username": {
            "type": "string",
            "description": "Username for which you would like to deny all open requests"
          },
          "reason": {
            "type": "string",
            "description": "A reason or comment why the requsts are being changed"
          }
        },
        "required": [
          "username"
        ]
      }
    },
    "example": {
      "properties": {
        "username": "test-username"
      }
    }
  }
}
```

Output Schema:

```
{
  "output": {
    "type": "object",
    "properties": {
      "rawResponse": {
        "type": "object"
      },
      "statusCode": {
        "type": "number"
      },
      "headers": {
        "type": "object"
      }
    }
  }
}
```

## Deny Pending Request by Hostname

Denies/cancels an active or pending request

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "hostname": {
            "type": "string",
            "description": "Name of the machine for which you would like to deny the session"
          },
          "reason": {
            "type": "string",
            "description": "A reason or comment why the requsts are being changed"
          }
        },
        "required": [
          "hostname"
        ]
      }
    },
    "example": {
      "properties": {
        "username": "test-hostname"
      }
    }
  }
}
```

Output Schema:

```
{
  "output": {
    "type": "object",
    "properties": {
      "rawResponse": {
        "type": "object"
      },
      "statusCode": {
        "type": "number"
      },
      "headers": {
        "type": "object"
      }
    }
  }
}
```


## Resources

For information and setup help, see the following sections of the BeyondTrust - Password Safe documentation:

* [BeyondTrust Password Safe Site](https://www.beyondtrust.com/products/password-safe)
