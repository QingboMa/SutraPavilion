

# 命令



![git](C:\Users\maqingbo\Pictures\git.jpg)

Repository:本地仓库

Remote:远程仓库

index:暂存区

workspace：工作区

```bash
$ git
usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           [--super-prefix=<path>] [--config-env=<name>=<envvar>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone     Clone a repository into a new directory
           usage: git clone [<options>] [--] <repo> [<dir>]

            -v, --verbose         be more verbose
            -q, --quiet           be more quiet
            --progress            force progress reporting
            --reject-shallow      don't clone shallow repository
            -n, --no-checkout     don't create a checkout
            --bare                create a bare repository
            --mirror              create a mirror repository (implies bare)
            -l, --local           to clone from a local repository
            --no-hardlinks        don't use local hardlinks, always copy
            -s, --shared          setup as shared repository
            --recurse-submodules[=<pathspec>]
                                  initialize submodules in the clone
            --recursive ...       alias of --recurse-submodules
            -j, --jobs <n>        number of submodules cloned in parallel
            --template <template-directory>
                                  directory from which templates will be used
            --reference <repo>    reference repository
            --reference-if-able <repo>
                                  reference repository
            --dissociate          use --reference only while cloning
            -o, --origin <name>   use <name> instead of 'origin' to track upstream
            -b, --branch <branch>
                                  checkout <branch> instead of the remote's HEAD
            -u, --upload-pack <path>
                                  path to git-upload-pack on the remote
            --depth <depth>       create a shallow clone of that depth
            --shallow-since <time>
                                  create a shallow clone since a specific time
            --shallow-exclude <revision>
                                  deepen history of shallow clone, excluding rev
            --single-branch       clone only one branch, HEAD or --branch
            --no-tags             don't clone any tags, and make later fetches not to follow them
            --shallow-submodules  any cloned submodules will be shallow
            --separate-git-dir <gitdir>
                                  separate git dir from working tree
            -c, --config <key=value>
                                  set config inside the new repository
            --server-option <server-specific>
                                  option to transmit
            -4, --ipv4            use IPv4 addresses only
            -6, --ipv6            use IPv6 addresses only
            --filter <args>       object filtering
            --remote-submodules   any cloned submodules will use their remote-tracking branch
            --sparse              initialize sparse-checkout file to include only files at root

   init      Create an empty Git repository or reinitialize an existing one
        usage: git init [-q | --quiet] [--bare] [--template=<template-directory>] [--shared[=<permissions>]] [<directory>]
            --template <template-directory>
                                  directory from which templates will be used
            --bare                create a bare repository
            --shared[=<permissions>]
                                  specify that the git repository is to be shared amongst several users
            -q, --quiet           be quiet
            --separate-git-dir <gitdir>
                                  separate git dir from working tree
            -b, --initial-branch <name>
                                  override the name of the initial branch
            --object-format <hash>
                                  specify the hash algorithm to use

work on the current change (see also: git help everyday)
   add       Add file contents to the index
            usage: git add [<options>] [--] <pathspec>...

            -n, --dry-run         dry run
            -v, --verbose         be verbose

            -i, --interactive     interactive picking
            -p, --patch           select hunks interactively
            -e, --edit            edit current diff and apply
            -f, --force           allow adding otherwise ignored files
            -u, --update          update tracked files
            --renormalize         renormalize EOL of tracked files (implies -u)
            -N, --intent-to-add   record only the fact that the path will be added later
            -A, --all             add changes from all tracked and untracked files
            --ignore-removal      ignore paths removed in the working tree (same as --no-all)
            --refresh             don't add, only refresh the index
            --ignore-errors       just skip files which cannot be added because of errors
            --ignore-missing      check if - even missing - files are ignored in dry run
            --sparse              allow updating entries outside of the sparse-checkout cone
            --chmod (+|-)x        override the executable bit of the listed files
            --pathspec-from-file <file>
                                  read pathspec from file
            --pathspec-file-nul   with --pathspec-from-file, pathspec elements are separated with NUL character

   mv        Move or rename a file, a directory, or a symlink
   restore   Restore working tree files
             git restore [<options>] [--source=<branch>] <file>...

                -s, --source <tree-ish>
                                      which tree-ish to checkout from
                -S, --staged          restore the index
                -W, --worktree        restore the working tree (default)
                --ignore-unmerged     ignore unmerged entries
                --overlay             use overlay mode
                -q, --quiet           suppress progress reporting
                --recurse-submodules[=<checkout>]
                                      control recursive updating of submodules
                --progress            force progress reporting
                -m, --merge           perform a 3-way merge with the new branch
                --conflict <style>    conflict style (merge or diff3)
                -2, --ours            checkout our version for unmerged files
                -3, --theirs          checkout their version for unmerged files
                -p, --patch           select hunks interactively
                --ignore-skip-worktree-bits
                                      do not limit pathspecs to sparse entries only
                --pathspec-from-file <file>
                                      read pathspec from file
                --pathspec-file-nul   with --pathspec-from-file, pathspec elements are separated with NUL character

   rm        Remove files from the working tree and from the index
           usage: git mv [<options>] <source>... <destination>

            -v, --verbose         be verbose
            -n, --dry-run         dry run
            -f, --force           force move/rename even if target exists
            -k                    skip move/rename errors
            --sparse              allow updating entries outside of the sparse-checkout cone


examine the history and state (see also: git help revisions)
   bisect    Use binary search to find the commit that introduced a bug
   diff      Show changes between commits, commit and working tree, etc
        usage: git <command> [<revision>...] -- [<file>...]
        
   grep      Print lines matching a pattern
           usage: git grep [<options>] [-e] <pattern> [<rev>...] [[--] <path>...]

            --cached              search in index instead of in the work tree
            --no-index            find in contents not managed by git
            --untracked           search in both tracked and untracked files
            --exclude-standard    ignore files specified via '.gitignore'
            --recurse-submodules  recursively search in each submodule

            -v, --invert-match    show non-matching lines
            -i, --ignore-case     case insensitive matching
            -w, --word-regexp     match patterns only at word boundaries
            -a, --text            process binary files as text
            -I                    don't match patterns in binary files
            --textconv            process binary files with textconv filters
            -r, --recursive       search in subdirectories (default)
            --max-depth <depth>   descend at most <depth> levels

            -E, --extended-regexp
                                  use extended POSIX regular expressions
            -G, --basic-regexp    use basic POSIX regular expressions (default)
            -F, --fixed-strings   interpret patterns as fixed strings
            -P, --perl-regexp     use Perl-compatible regular expressions

            -n, --line-number     show line numbers
            --column              show column number of first match
            -h                    don't show filenames
            -H                    show filenames
            --full-name           show filenames relative to top directory
            -l, --files-with-matches
                                  show only filenames instead of matching lines
            --name-only           synonym for --files-with-matches
            -L, --files-without-match
                                  show only the names of files without match
            -z, --null            print NUL after filenames
            -o, --only-matching   show only matching parts of a line
            -c, --count           show the number of matches instead of matching lines
            --color[=<when>]      highlight matches
            --break               print empty line between matches from different files
            --heading             show filename only once above matches from same file

            -C, --context <n>     show <n> context lines before and after matches
            -B, --before-context <n>
                                  show <n> context lines before matches
            -A, --after-context <n>
                                  show <n> context lines after matches
            --threads <n>         use <n> worker threads
            -NUM                  shortcut for -C NUM
            -p, --show-function   show a line with the function name before matches
            -W, --function-context
                                  show the surrounding function

            -f <file>             read patterns from file
            -e <pattern>          match <pattern>
            --and                 combine patterns specified with -e
            --or
            --not
            (
            )
            -q, --quiet           indicate hit with exit status without output
            --all-match           show only matches from files that match all patterns

            -O, --open-files-in-pager[=<pager>]
                                  show matching files in the pager
            --ext-grep            allow calling of grep(1) (ignored by this build)
            
   log       Show commit logs
          usage: git <command> [<revision>...] -- [<file>...]
          
   show      Show various types of objects
          usage: git <command> [<revision>...] -- [<file>...]
   status    Show the working tree status
        usage: git status [<options>] [--] <pathspec>...

            -v, --verbose         be verbose
            -s, --short           show status concisely
            -b, --branch          show branch information
            --show-stash          show stash information
            --ahead-behind        compute full ahead/behind values
            --porcelain[=<version>]
                                  machine-readable output
            --long                show status in long format (default)
            -z, --null            terminate entries with NUL
            -u, --untracked-files[=<mode>]
                                  show untracked files, optional modes: all, normal, no. (Default: all)
            --ignored[=<mode>]    show ignored files, optional modes: traditional, matching, no. (Default: traditional)
            --ignore-submodules[=<when>]
                                  ignore changes to submodules, optional when: all, dirty, untracked. (Default: all)
            --column[=<style>]    list untracked files in columns
            --no-renames          do not detect renames
            -M, --find-renames[=<n>]
                                  detect renames, optionally set similarity index
            --show-ignored-directory
                                  (DEPRECATED: use --ignore=matching instead) Only show directories that match an ignore pattern name.
            --no-lock-index       (DEPRECATED: use `git --no-optional-locks status` instead) Do not lock the index

grow, mark and tweak your common history
   branch    List, create, or delete branches
           usage: git branch [<options>] [-r | -a] [--merged] [--no-merged]
           or: git branch [<options>] [-l] [-f] <branch-name> [<start-point>]
           or: git branch [<options>] [-r] (-d | -D) <branch-name>...
           or: git branch [<options>] (-m | -M) [<old-branch>] <new-branch>
           or: git branch [<options>] (-c | -C) [<old-branch>] <new-branch>
           or: git branch [<options>] [-r | -a] [--points-at]
           or: git branch [<options>] [-r | -a] [--format]

        Generic options
            -v, --verbose         show hash and subject, give twice for upstream branch
            -q, --quiet           suppress informational messages
            -t, --track           set up tracking mode (see git-pull(1))
            -u, --set-upstream-to <upstream>
                                  change the upstream info
            --unset-upstream      unset the upstream info
            --color[=<when>]      use colored output
            -r, --remotes         act on remote-tracking branches
            --contains <commit>   print only branches that contain the commit
            --no-contains <commit>
                                  print only branches that don't contain the commit
            --abbrev[=<n>]        use <n> digits to display object names

        Specific git-branch actions:
            -a, --all             list both remote-tracking and local branches
            -d, --delete          delete fully merged branch
            -D                    delete branch (even if not merged)
            -m, --move            move/rename a branch and its reflog
            -M                    move/rename a branch, even if target exists
            -c, --copy            copy a branch and its reflog
            -C                    copy a branch, even if target exists
            -l, --list            list branch names
            --show-current        show current branch name
            --create-reflog       create the branch's reflog
            --edit-description    edit the description for the branch
            -f, --force           force creation, move/rename, deletion
            --merged <commit>     print only branches that are merged
            --no-merged <commit>  print only branches that are not merged
            --column[=<style>]    list branches in columns
            --sort <key>          field name to sort on
            --points-at <object>  print only branches of the object
            -i, --ignore-case     sorting and filtering are case insensitive
            --format <format>     format to use for the output

   commit    Record changes to the repository
           usage: git commit [<options>] [--] <pathspec>...

            -q, --quiet           suppress summary after successful commit
            -v, --verbose         show diff in commit message template

        Commit message options
            -F, --file <file>     read message from file
            --author <author>     override author for commit
            --date <date>         override date for commit
            -m, --message <message>
                                  commit message
            -c, --reedit-message <commit>
                                  reuse and edit message from specified commit
            -C, --reuse-message <commit>
                                  reuse message from specified commit
            --fixup [(amend|reword):]commit
                                  use autosquash formatted message to fixup or amend/reword specified commit
            --squash <commit>     use autosquash formatted message to squash specified commit
            --reset-author        the commit is authored by me now (used with -C/-c/--amend)
            --trailer <trailer>   add custom trailer(s)
            -s, --signoff         add a Signed-off-by trailer
            -t, --template <file>
                                  use specified template file
            -e, --edit            force edit of commit
            --cleanup <mode>      how to strip spaces and #comments from message
            --status              include status in commit message template
            -S, --gpg-sign[=<key-id>]
                                  GPG sign commit

        Commit contents options
            -a, --all             commit all changed files
            -i, --include         add specified files to index for commit
            --interactive         interactively add files
            -p, --patch           interactively add changes
            -o, --only            commit only specified files
            -n, --no-verify       bypass pre-commit and commit-msg hooks
            --dry-run             show what would be committed
            --short               show status concisely
            --branch              show branch information
            --ahead-behind        compute full ahead/behind values
            --porcelain           machine-readable output
            --long                show status in long format (default)
            -z, --null            terminate entries with NUL
            --amend               amend previous commit
            --no-post-rewrite     bypass post-rewrite hook
            -u, --untracked-files[=<mode>]
                                  show untracked files, optional modes: all, normal, no. (Default: all)
            --pathspec-from-file <file>
                                  read pathspec from file
            --pathspec-file-nul   with --pathspec-from-file, pathspec elements are separated with NUL character

   merge     Join two or more development histories together
           usage: git merge [<options>] [<commit>...]
           or: git merge --abort
           or: git merge --continue

            -n                    do not show a diffstat at the end of the merge
            --stat                show a diffstat at the end of the merge
            --summary             (synonym to --stat)
            --log[=<n>]           add (at most <n>) entries from shortlog to merge commit message
            --squash              create a single commit instead of doing a merge
            --commit              perform a commit if the merge succeeds (default)
            -e, --edit            edit message before committing
            --cleanup <mode>      how to strip spaces and #comments from message
            --ff                  allow fast-forward (default)
            --ff-only             abort if fast-forward is not possible
            --rerere-autoupdate   update the index with reused conflict resolution if possible
            --verify-signatures   verify that the named commit has a valid GPG signature
            -s, --strategy <strategy>
                                  merge strategy to use
            -X, --strategy-option <option=value>
                                  option for selected merge strategy
            -m, --message <message>
                                  merge commit message (for a non-fast-forward merge)
            -F, --file <path>     read message from file
            -v, --verbose         be more verbose
            -q, --quiet           be more quiet
            --abort               abort the current in-progress merge
            --quit                --abort but leave index and working tree alone
            --continue            continue the current in-progress merge
            --allow-unrelated-histories
                                  allow merging unrelated histories
            --progress            force progress reporting
            -S, --gpg-sign[=<key-id>]
                                  GPG sign commit
            --autostash           automatically stash/stash pop before and after
            --overwrite-ignore    update ignored files (default)
            --signoff             add a Signed-off-by trailer
            --no-verify           bypass pre-merge-commit and commit-msg hooks



   rebase    Reapply commits on top of another base tip
           usage: git rebase [-i] [options] [--exec <cmd>] [--onto <newbase> | --keep-base] [<upstream> [<branch>]]
           or: git rebase [-i] [options] [--exec <cmd>] [--onto <newbase>] --root [<branch>]
           or: git rebase --continue | --abort | --skip | --edit-todo

            --onto <revision>     rebase onto given branch instead of upstream
            --keep-base           use the merge-base of upstream and branch as the current base
            --no-verify           allow pre-rebase hook to run
            -q, --quiet           be quiet. implies --no-stat
            -v, --verbose         display a diffstat of what changed upstream
            -n, --no-stat         do not show diffstat of what changed upstream
            --signoff             add a Signed-off-by trailer to each commit
            --committer-date-is-author-date
                                  make committer date match author date
            --reset-author-date   ignore author date and use current date
            -C <n>                passed to 'git apply'
            --ignore-whitespace   ignore changes in whitespace
            --whitespace <action>
                                  passed to 'git apply'
            -f, --force-rebase    cherry-pick all commits, even if unchanged
            --no-ff               cherry-pick all commits, even if unchanged
            --continue            continue
            --skip                skip current patch and continue
            --abort               abort and check out the original branch
            --quit                abort but keep HEAD where it is
            --edit-todo           edit the todo list during an interactive rebase
            --show-current-patch  show the patch file being applied or merged
            --apply               use apply strategies to rebase
            -m, --merge           use merging strategies to rebase
            -i, --interactive     let the user edit the list of commits to rebase
            --rerere-autoupdate   update the index with reused conflict resolution if possible
            --empty <{drop,keep,ask}>
                                  how to handle commits that become empty
            --autosquash          move commits that begin with squash!/fixup! under -i
            -S, --gpg-sign[=<key-id>]
                                  GPG-sign commits
            --autostash           automatically stash/stash pop before and after
            -x, --exec <exec>     add exec lines after each commit of the editable list
            -r, --rebase-merges[=<mode>]
                                  try to rebase merges instead of skipping them
            --fork-point          use 'merge-base --fork-point' to refine upstream
            -s, --strategy <strategy>
                                  use the given merge strategy
            -X, --strategy-option <option>
                                  pass the argument through to the merge strategy
            --root                rebase all reachable commits up to the root(s)
            --reschedule-failed-exec
                                  automatically re-schedule any `exec` that fails
            --reapply-cherry-picks
                                  apply all changes, even those already present upstream



   reset     Reset current HEAD to the specified state
           usage: git reset [--mixed | --soft | --hard | --merge | --keep] [-q] [<commit>]
           or: git reset [-q] [<tree-ish>] [--] <pathspec>...
           or: git reset [-q] [--pathspec-from-file [--pathspec-file-nul]] [<tree-ish>]
           or: git reset --patch [<tree-ish>] [--] [<pathspec>...]
           or: DEPRECATED: git reset [-q] [--stdin [-z]] [<tree-ish>]

            -q, --quiet           be quiet, only report errors
            --mixed               reset HEAD and index
            --soft                reset only HEAD
            --hard                reset HEAD, index and working tree
            --merge               reset HEAD, index and working tree
            --keep                reset HEAD but keep local changes
            --recurse-submodules[=<reset>]
                                  control recursive updating of submodules
            -p, --patch           select hunks interactively
            -N, --intent-to-add   record only the fact that removed paths will be added later
            --pathspec-from-file <file>
                                  read pathspec from file
            --pathspec-file-nul   with --pathspec-from-file, pathspec elements are separated with NUL character
            -z                    DEPRECATED (use --pathspec-file-nul instead): paths are separated with NUL 									character
            --stdin               DEPRECATED (use --pathspec-from-file=- instead): read paths from <stdin>

   switch    Switch branches
           usage: git switch [<options>] [<branch>]

            -c, --create <branch>
                                  create and switch to a new branch
            -C, --force-create <branch>
                                  create/reset and switch to a branch
            --guess               second guess 'git switch <no-such-branch>'
            --discard-changes     throw away local modifications
            -q, --quiet           suppress progress reporting
            --recurse-submodules[=<checkout>]
                                  control recursive updating of submodules
            --progress            force progress reporting
            -m, --merge           perform a 3-way merge with the new branch
            --conflict <style>    conflict style (merge or diff3)
            -d, --detach          detach HEAD at named commit
            -t, --track           set upstream info for new branch
            -f, --force           force checkout (throw away local modifications)
            --orphan <new-branch>
                                  new unparented branch
            --overwrite-ignore    update ignored files (default)
            --ignore-other-worktrees
                                  do not check if another worktree is holding the given ref


   tag       Create, list, delete or verify a tag object signed with GPG
           usage: git tag [-a | -s | -u <key-id>] [-f] [-m <msg> | -F <file>]
                       <tagname> [<head>]
           or: git tag -d <tagname>...
           or: git tag -l [-n[<num>]] [--contains <commit>] [--no-contains <commit>] [--points-at <object>]
                       [--format=<format>] [--merged <commit>] [--no-merged <commit>] [<pattern>...]
           or: git tag -v [--format=<format>] <tagname>...

            -l, --list            list tag names
            -n[<n>]               print <n> lines of each tag message
            -d, --delete          delete tags
            -v, --verify          verify tags

        Tag creation options
            -a, --annotate        annotated tag, needs a message
            -m, --message <message>
                                  tag message
            -F, --file <file>     read message from file
            -e, --edit            force edit of tag message
            -s, --sign            annotated and GPG-signed tag
            --cleanup <mode>      how to strip spaces and #comments from message
            -u, --local-user <key-id>
                                  use another key to sign the tag
            -f, --force           replace the tag if exists
            --create-reflog       create a reflog

        Tag listing options
            --column[=<style>]    show tag list in columns
            --contains <commit>   print only tags that contain the commit
            --no-contains <commit>
                                  print only tags that don't contain the commit
            --merged <commit>     print only tags that are merged
            --no-merged <commit>  print only tags that are not merged
            --sort <key>          field name to sort on
            --points-at <object>  print only tags of the object
            --format <format>     format to use for the output
            --color[=<when>]      respect format colors
            -i, --ignore-case     sorting and filtering are case insensitive



collaborate (see also: git help workflows)
   fetch     Download objects and refs from another repository
           usage: git fetch [<options>] [<repository> [<refspec>...]]
           or: git fetch [<options>] <group>
           or: git fetch --multiple [<options>] [(<repository> | <group>)...]
           or: git fetch --all [<options>]

            -v, --verbose         be more verbose
            -q, --quiet           be more quiet
            --all                 fetch from all remotes
            --set-upstream        set upstream for git pull/fetch
            -a, --append          append to .git/FETCH_HEAD instead of overwriting
            --atomic              use atomic transaction to update references
            --upload-pack <path>  path to upload pack on remote end
            -f, --force           force overwrite of local reference
            -m, --multiple        fetch from multiple remotes
            -t, --tags            fetch all tags and associated objects
            -n                    do not fetch all tags (--no-tags)
            -j, --jobs <n>        number of submodules fetched in parallel
            --prefetch            modify the refspec to place all refs within refs/prefetch/
            -p, --prune           prune remote-tracking branches no longer on remote
            -P, --prune-tags      prune local tags no longer on remote and clobber changed tags
            --recurse-submodules[=<on-demand>]
                                  control recursive fetching of submodules
            --dry-run             dry run
            --write-fetch-head    write fetched references to the FETCH_HEAD file
            -k, --keep            keep downloaded pack
            -u, --update-head-ok  allow updating of HEAD ref
            --progress            force progress reporting
            --depth <depth>       deepen history of shallow clone
            --shallow-since <time>
                                  deepen history of shallow repository based on time
            --shallow-exclude <revision>
                                  deepen history of shallow clone, excluding rev
            --deepen <n>          deepen history of shallow clone
            --unshallow           convert to a complete repository
            --update-shallow      accept refs that update .git/shallow
            --refmap <refmap>     specify fetch refmap
            -o, --server-option <server-specific>
                                  option to transmit
            -4, --ipv4            use IPv4 addresses only
            -6, --ipv6            use IPv6 addresses only
            --negotiation-tip <revision>
                                  report that we have only objects reachable from this object
            --negotiate-only      do not fetch a packfile; instead, print ancestors of negotiation tips
            --filter <args>       object filtering
            --auto-maintenance    run 'maintenance --auto' after fetching
            --auto-gc             run 'maintenance --auto' after fetching
            --show-forced-updates
                                  check for forced-updates on all updated branches
            --write-commit-graph  write the commit-graph after fetching
            --stdin               accept refspecs from stdin



   pull      Fetch from and integrate with another repository or a local branch
           usage: git pull [<options>] [<repository> [<refspec>...]]

            -v, --verbose         be more verbose
            -q, --quiet           be more quiet
            --progress            force progress reporting
            --recurse-submodules[=<on-demand>]
                                  control for recursive fetching of submodules

        Options related to merging
            -r, --rebase[=(false|true|merges|interactive)]
                                  incorporate changes by rebasing rather than merging
            -n                    do not show a diffstat at the end of the merge
            --stat                show a diffstat at the end of the merge
            --log[=<n>]           add (at most <n>) entries from shortlog to merge commit message
            --signoff[=...]       add a Signed-off-by trailer
            --squash              create a single commit instead of doing a merge
            --commit              perform a commit if the merge succeeds (default)
            --edit                edit message before committing
            --cleanup <mode>      how to strip spaces and #comments from message
            --ff                  allow fast-forward
            --ff-only             abort if fast-forward is not possible
            --verify              control use of pre-merge-commit and commit-msg hooks
            --verify-signatures   verify that the named commit has a valid GPG signature
            --autostash           automatically stash/stash pop before and after
            -s, --strategy <strategy>
                                  merge strategy to use
            -X, --strategy-option <option=value>
                                  option for selected merge strategy
            -S, --gpg-sign[=<key-id>]
                                  GPG sign commit
            --allow-unrelated-histories
                                  allow merging unrelated histories

        Options related to fetching
            --all                 fetch from all remotes
            -a, --append          append to .git/FETCH_HEAD instead of overwriting
            --upload-pack <path>  path to upload pack on remote end
            -f, --force           force overwrite of local branch
            -t, --tags            fetch all tags and associated objects
            -p, --prune           prune remote-tracking branches no longer on remote
            -j, --jobs[=<n>]      number of submodules pulled in parallel
            --dry-run             dry run
            -k, --keep            keep downloaded pack
            --depth <depth>       deepen history of shallow clone
            --shallow-since <time>
                                  deepen history of shallow repository based on time
            --shallow-exclude <revision>
                                  deepen history of shallow clone, excluding rev
            --deepen <n>          deepen history of shallow clone
            --unshallow           convert to a complete repository
            --update-shallow      accept refs that update .git/shallow
            --refmap <refmap>     specify fetch refmap
            -o, --server-option <server-specific>
                                  option to transmit
            -4, --ipv4            use IPv4 addresses only
            -6, --ipv6            use IPv6 addresses only
            --negotiation-tip <revision>
                                  report that we have only objects reachable from this object
            --show-forced-updates
                                  check for forced-updates on all updated branches
            --set-upstream        set upstream for git pull/fetch


   push      Update remote refs along with associated objects
        usage: git push [<options>] [<repository> [<refspec>...]]

            -v, --verbose         be more verbose
            -q, --quiet           be more quiet
            --repo <repository>   repository
            --all                 push all refs
            --mirror              mirror all refs
            -d, --delete          delete refs
            --tags                push tags (can't be used with --all or --mirror)
            -n, --dry-run         dry run
            --porcelain           machine-readable output
            -f, --force           force updates
            --force-with-lease[=<refname>:<expect>]
                                  require old value of ref to be at this value
            --force-if-includes   require remote updates to be integrated locally
            --recurse-submodules (check|on-demand|no)
                                  control recursive pushing of submodules
            --thin                use thin pack
            --receive-pack <receive-pack>
                                  receive pack program
            --exec <receive-pack>
                                  receive pack program
            -u, --set-upstream    set upstream for git pull/status
            --progress            force progress reporting
            --prune               prune locally removed refs
            --no-verify           bypass pre-push hook
            --follow-tags         push missing but relevant tags
            --signed[=(yes|no|if-asked)]
                                  GPG sign the push
            --atomic              request atomic transaction on remote side
            -o, --push-option <server-specific>
                                  option to transmit
            -4, --ipv4            use IPv4 addresses only
            -6, --ipv6            use IPv6 addresses only

-------------------------------------------------------------------------------------------------------------------
'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.
See 'git help git' for an overview of the system.

```



## 常用命令

### 1、查询提交日志（简洁）

，不加 ` --pretty=oneline` 会有很多提交信息

```bash
$ git log --pretty=oneline
```





### 2、回退版本

```bash
git reset --hard 版本号 
```



### 3、删除index区的文件

删除index区的文件`t1.txt`,需要先`git add t1.txt`

```bash
git rm --cached t1.txt
```



### 4、删除本地仓库的文件

也就是真实文件



``` bash
 git rm -f t1.txt

```

### 5、还原到上次commit到本地仓库

已经commit到工作区中的文件`a.c`修改后,并且没有add到index时，需要还原到上次commit到本地仓库之后的状态

```bash
git restore a.c
```

将暂存区的a.c删除，不会改变工作区中的a.c

```bash
git restore --staged  a.c
```

