import re

def check_password_complexity(password):
    has_uppercase = False
    has_lowercase = False
    has_digit = False
    has_special_char = False
    
    if re.search(r'[A-Z]', password):
        has_uppercase = True
    
    if re.search(r'[a-z]', password):
        has_lowercase = True
    
    if re.search(r'\d', password):
        has_digit = True
    
    if re.search(r'[\W_]', password):
        has_special_char = True
    
    strength = "Weak"
    
    if len(password) >= 8:
        if has_uppercase and has_lowercase and has_digit and has_special_char:
            strength = "Strong"
        elif (has_uppercase and has_lowercase) or (has_digit and has_special_char):
            strength = "Medium"
    
    return {
        "has_uppercase": has_uppercase,
        "has_lowercase": has_lowercase,
        "has_digit": has_digit,
        "has_special_char": has_special_char,
        "strength": strength
    }

def main():
    password = input("Enter your password: ")
    result = check_password_complexity(password)
    
    print(f"\nPassword Analysis:")
    print(f"Contains uppercase: {result['has_uppercase']}")
    print(f"Contains lowercase: {result['has_lowercase']}")
    print(f"Contains digit: {result['has_digit']}")
    print(f"Contains special character: {result['has_special_char']}")
    print(f"Password strength: {result['strength']}")

if __name__ == "__main__":
    main()
