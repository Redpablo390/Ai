      - name: Install Android SDK packages and accept licenses
        run: |
          SDKMANAGER="$ANDROID_HOME/cmdline-tools/latest/bin/sdkmanager"
          if [ ! -x "$SDKMANAGER" ]; then
            echo "sdkmanager not found"
            find "$ANDROID_HOME/cmdline-tools" -name sdkmanager -type f
            exit 1
          fi
          yes | "$SDKMANAGER" --licenses
          "$SDKMANAGER" "platforms;android-35" "build-tools;35.0.0"
