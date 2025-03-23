# Why do python3 and pip3 still exist on macOS?

Since macOS 12.3, there’s no more `python` — only `python3`. That’s because [Apple removed Python 2](https://developer.apple.com/documentation/macos-release-notes/macos-12_3-release-notes#Python), but for historical reasons, the `3` remains in the command.

The same goes for `pip3`. Back in the day, `pip` was for Python 2, and `pip3` was for Python 3. Now that Python 2 is gone, only Python 3 remains, but `pip3` is still around because many tutorials and scripts use it.

💡 **Fix**: If you’re tired of typing the extra `3`:

```
echo 'alias python="python3"' >> ~/.zshrc  
echo 'alias pip="pip3"' >> ~/.zshrc  
source ~/.zshrc  
```

Now you can just use `python` and `pip`.
