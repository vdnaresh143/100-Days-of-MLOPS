# Day 3: Fix a Broken uv Lockfile Specification

The xFusionCorp Industries ML team uses uv and lockfiles to keep Python dependencies reproducible across machines. A teammate has left behind a requirements.in specification that does not match the team's standard. Correct it and compile it into a pinned lockfile.


A high-level dependency specification exists at /root/code/fraud-detection/requirements.in. uv is already installed.

The corrected specification must meet the following requirements:

it lists exactly these four top-level packages: scikit-learn, mlflow, pandas, and numpy;
every package carries a version constraint that uv can actually satisfy against PyPI.
Review the existing requirements.in, and correct everything that does not match the requirements above.

From the project directory, compile the corrected specification into a pinned lockfile:

   uv pip compile requirements.in -o requirements.txt

The resulting requirements.txt must pin each of the four top-level packages to an exact version using ==, and must also include the transitive dependencies that uv resolved.

# Solution:

cd /root/code/fraud-detection/
cat requirements.in

cat <<EOF > requirements.in
scikit-learn>=1.0
mlflow>=2.0
pandas>=2.0
numpy>=1.21
EOF

Note: Using >= allows uv to resolve the best compatible versions against PyPI while still strictly adhering to the "exactly these four" top-level package rule.

Compile the Pinned Lockfile
uv pip compile requirements.in -o requirements.txt

Verify the Output
grep -E "^(scikit-learn|mlflow|pandas|numpy)==" requirements.txt


