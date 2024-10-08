# Write-a-program-for-determination-of-marginal-distribution-of-X-Y-.
% Example Joint Probability Distribution (4x4 matrix for 4 symbols)
P_XY = [0.1 0.05 0.05 0.1;
        0.05 0.2  0.1  0.05;
        0.05 0.05 0.1  0.1;
        0.1  0.05 0.05 0.1];

% Marginal Distributions
P_X = sum(P_XY, 2);  % Sum over columns for X
P_Y = sum(P_XY, 1);  % Sum over rows for Y

% Marginal Entropies
H_X = -sum(P_X .* log2(P_X + (P_X == 0)));  % H(X)
H_Y = -sum(P_Y .* log2(P_Y + (P_Y == 0)));  % H(Y)

% Joint Entropy H(X, Y)
H_XY = -sum(sum(P_XY .* log2(P_XY + (P_XY == 0))));

% Conditional Entropies
H_X_given_Y = H_XY - H_Y;  % H(X|Y)
H_Y_given_X = H_XY - H_X;  % H(Y|X)

% Mutual Information I(X; Y)
I_XY = H_X + H_Y - H_XY;

% Display Results
fprintf('Marginal Distribution P(X):\n');
disp(P_X');
fprintf('Marginal Distribution P(Y):\n');
disp(P_Y);
fprintf('Marginal Entropy H(X): %f\n', H_X);
fprintf('Marginal Entropy H(Y): %f\n', H_Y);
fprintf('Joint Entropy H(X, Y): %f\n', H_XY);
fprintf('Conditional Entropy H(X|Y): %f\n', H_X_given_Y);
fprintf('Conditional Entropy H(Y|X): %f\n', H_Y_given_X);
fprintf('Mutual Information I(X; Y): %f\n', I_XY);
