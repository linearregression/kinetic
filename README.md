Kinetic
=======

Kinetic is an erlang Kinesis client built to be an OTP application and
easy to integrate and work with.

If you are running Kinetic from an EC2 instance with an IAM role it
essentially doesn't need any configuration as it will be smart enough to
grab everything from the context. At the same time it will be possible
to override the context values with configured ones.

You can start an erl with:

    $ erl -pa ebin -pa deps/*/ebin -s inets -s crypto -s ssl -s lhttpc -config development -s kinetic
    Erlang R16B03-1 (erts-5.10.4) [source] [64-bit] [smp:4:4] [async-threads:10] [hipe] [kernel-poll:false] [dtrace]

    Eshell V5.10.4  (abort with ^G)
    1> kinetic:list_streams([]).
    {ok, [{<<"HasMoreStreams">>,false},{<<"StreamNames">>,[]}]}

`development.config` allows the developer to override some configuration
values to allow for different setups.


To Build a release
We use git tag as the cutoff of what a release should look like.
So before making a release:
- make sure you create a tag to freeze the whole state of code in master branch
  example:
  -- git tag -a 1.0.0 -m "Version 1.0.0 release. Brief comments"
  -- git push --tag 1.0.0
  to check git tag
- You may be in DETACHED stage, so you want to create a branch with the tag
  -- git checkout -b 1.0.1-release 1.0.0

Then compile and make a otp release as usual.
To check vsn in ebin/kinetic.app should be the same as your git tag



