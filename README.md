Splash MainActivity 4 seconds and Intent to LoginActivity after setting up SharedPreferences 'logIn' key 'flag' to flase

      new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                SharedPreferences pref = getSharedPreferences("logIn", MODE_PRIVATE);
                Boolean check = pref.getBoolean("flag", false);

                Intent iNext;

                if(check)
                {
                    iNext = new Intent(MainActivity.this, HomeActivity.class);
                }
                else
                {
                    iNext = new Intent(MainActivity.this, LogInActivity.class);
                }

                startActivity(iNext);
            }
        }, 4000);

On Click LogIn setting SharedPreferences 'logIn' key 'flag' to true and Intent to HomeActivity

        loginButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                SharedPreferences pref = getSharedPreferences("logIn", MODE_PRIVATE);
                SharedPreferences.Editor edit = pref.edit();
                edit.putBoolean("flag", true);
                edit.apply();

                Intent home = new Intent(LogInActivity.this, HomeActivity.class);
                startActivity(home);
            }
        });

On Click LogOut setting SharedPreferences 'logIn' key 'flag' to false and Intent to LoginActivity

        logoutButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                SharedPreferences pref = getSharedPreferences("logIn", MODE_PRIVATE);
                SharedPreferences.Editor edit = pref.edit();
                edit.putBoolean("flag", false);
                edit.apply();

                Intent loginPage = new Intent(HomeActivity.this, LogInActivity.class);
                startActivity(loginPage);
            }
        });
        
