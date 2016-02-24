# Rebase previous commits

I had just realised that the AWS IAM admin credentials I had previously kept reminding myself not to commit, had been commited. Rookie move!

Luckily, I had yet to push remotely to GitHub so was in a good position to remove the offending credentails without too much bother. Yes, the details could have been revoked via the AWS admin console and the code pushed anyway, but we have scanners in place that would have flagged the repo and I'd soon have to explain why AWS credentials, revoked or otherwise, had been commited.

Rebase to the rescue! Listing the last three commits using ```git rebase -i @~3```, I could pick the commit I wished to amend and remove the credentials. From the list, I changed the commit in question from 'pick' to 'edit' and Git reverted back to that point in history. Having removed the credentials from file in question, the file was added readded , ```git add <file>```, and ```git commit --amend``` was ran to update the commit. I could finally ```git push``` with peace of mind.

In the case above, the commit was 3 commits prior. If it was the last commit and no code had been pushed, another useful command would be ```git reset @~```. This discards the last commit without editing your files allowing you to compose the commit again.
