# Gundowebcity
Hi world this is my profile
Consult for your bussiness website
web testing
from flask import Flask, request, jsonify
import re
app = Flask(__name__)
def is_strong_password(password):
    # Password must be at least 8 characters long
    if len(password) < 8:
        return False
    # Password must contain at least one uppercase letter
    if not re.search(r'[A-Z]', password):
        return False
    # Password must contain at least one lowercase letter
    if not re.search(r'[a-z]', password):
        return False
    # Password must contain at least one digit
    if not re.search(r'\d', password):
        return False
    # Password must contain at least one special character
    if not re.search(r'[!@#$%^&*(),.?":{}|<>]', password):
        return False
    return True

@app.route('/signup', methods=['POST'])
def signup():
    data = request.get_json()
    username = data.get('username')
    password = data.get('password')

    if not username or not password:
        return jsonify({'error': 'Username and password are required'}), 400

    if not is_strong_password(password):
        return jsonify({'error': 'Password is not strong enough'}), 400

    # Here you might add code to save the user to a database

    return jsonify({'message': 'User signed up successfully'}), 200

if __name__ == '__main__':
    app.run(debug=True)




fast service


