# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:
```
#include <stdio.h>
#include <math.h>

// Function to calculate (a^b) mod P using modular exponentiation
long long int power(long long int a, long long int b, long long int P)
{
    long long int result = 1;
    a = a % P;

    while (b > 0)
    {
        if (b % 2 == 1)
            result = (result * a) % P;

        b = b / 2;
        a = (a * a) % P;
    }
    return result;
}

int main()
{
    long long int P, G, a, b, x, y, ka, kb;

    printf("\n*****Diffie-Hellman Key Exchange Algorithm*****\n\n");

    // Publicly shared prime number and primitive root
    printf("Enter the value of P: ");
    scanf("%lld", &P);
    printf("The value of P: %lld\n", P);

    printf("Enter the value of G (Primitive root of P): ");
    scanf("%lld", &G);
    printf("The value of G: %lld\n\n", G);

    // Alice chooses her private key 'a'
    a = 4;
    printf("The private key a for Alice : %lld\n", a);
    x = power(G, a, P);  // Alice's public key

    // Bob chooses his private key 'b'
    b = 3;
    printf("The private key b for Bob : %lld\n\n", b);
    y = power(G, b, P);  // Bob's public key

    // After exchanging public keys, both compute the shared secret key
    ka = power(y, a, P); // Secret key for Alice
    kb = power(x, b, P); // Secret key for Bob

    printf("Secret key for the Alice is : %lld\n", ka);
    printf("Secret Key for the Bob is : %lld\n", kb);

    return 0;
}
```

## Output:

<img width="1909" height="1143" alt="image" src="https://github.com/user-attachments/assets/8229e155-0f05-46e3-b24b-3263e46c9936" />


## Result:
  The program is executed successfully

