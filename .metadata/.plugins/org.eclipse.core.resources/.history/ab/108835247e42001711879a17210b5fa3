import java.util.ArrayList;
import java.util.Arrays;

/**
 * 
 */

/**
 * This class produces the result of the battles
 * 
 * @author mariachowdhury
 *
 */
public class Battle {
	/**
	 * sort list according to rank
	 * 
	 * @param ArrayList
	 * @return ArrayList
	 */
	public ArrayList<Transformer> getSortedList(
			ArrayList<Transformer> transformers) {
		Transformer[] transformersArr = transformers
				.toArray(new Transformer[0]);
		Arrays.sort(transformersArr);
		ArrayList<Transformer> transformersList = new ArrayList<Transformer>(
				Arrays.asList(transformersArr));
		return transformersList;
	}

	/**
	 * checking Special rules
	 * 
	 * @param ArrayList
	 *            of Transformers
	 * @return true if there exists "Optimus Prime" or "Predaking"
	 */
	public boolean specialRuleApplies(ArrayList<Transformer> transformersList) {
		for (int k = 0; k < transformersList.size(); k++) {
			if (transformersList.get(k).getName().equals("Optimus Prime")
					|| transformersList.get(k).getName().equals("Predaking")) {
				return true;
			}
		}
		return false;

	}

	/**
	 * print special rules winner
	 * 
	 * @param ArrayList
	 *            of Transformers
	 * @return the name of the winning team. if one of "Optimus Prime" or
	 *         "Predaking" exists then that one is the winner else more
	 *         occurrences of one of them determines the winner
	 */
	public String printSpecialWinner(ArrayList<Transformer> transformersList) {
		String teamname = "";
		ArrayList<Transformer> transformerSpecial = new ArrayList<Transformer>();
		for (int k = 0; k < transformersList.size(); k++) {
			if (transformersList.get(k).getName().equals("Optimus Prime")
					|| transformersList.get(k).getName().equals("Predaking")) {
				transformerSpecial.add(transformersList.get(k));
			}
		}

		int countOptimus = 0;
		int countPredaking = 0;
		for (int i = 0; i < transformerSpecial.size(); i++) {
			Transformer transformer = transformerSpecial.get(i);
			if (transformer.getName().equals("Optimus Prime")) {

				countOptimus++;
			} else {
				countPredaking++;
			}
		}
		if (countPredaking == countOptimus) {
			teamname = "does not exist. Both competitors destroyed";
		} else if (countOptimus > countPredaking) {
			teamname = "Optimus Prime";
		} else {
			teamname = "Predaking";
		}
		return teamname;
	}

	/**
	 * Comparing two transformers based on courage and strength value
	 * 
	 * @param transformeri
	 * @param transformerj
	 * @return higher value Transformer is returned. If any fighter is down 4 or
	 *         more points of courage and 3 or more points of strength compared
	 *         to their opponent, the opponent automatically wins the face-off
	 */
	public Transformer compareBasedOnCourage(Transformer transformeri,
			Transformer transformerj) {
		if (transformeri.getType() == transformerj.getType()) {
			return null;
		}
		if ((transformeri.courage > transformerj.courage)) {
			if ((transformeri.courage - transformerj.courage) >= 4
					&& (transformeri.strength - transformerj.strength) >= 3) {
				return transformerj;
			}
		} else if (transformerj.courage > transformeri.courage) {
			if ((transformerj.courage - transformeri.courage) >= 4
					&& (transformerj.strength - transformeri.strength) >= 3) {
				return transformeri;
			}
		}
		return null;
	}

	/**
	 * Comparing two transformers based on skill
	 * 
	 * @param transformeri
	 * @param transformerj
	 * @return higher value Transformer is returned. if one of the fighters is 3
	 *         or more points of skill above their opponent, they win the fight
	 */
	public Transformer compareBasedOnSkill(Transformer transformeri,
			Transformer transformerj) {
		if (transformeri.getType() == transformerj.getType()) {
			return null;
		}
		if (transformeri.skill > transformerj.skill) {
			if ((transformeri.skill - transformerj.skill) >= 3) {
				return transformerj;
			}
		} else if (transformerj.skill > transformeri.skill) {
			if ((transformerj.skill - transformeri.skill) >= 3) {
				return transformeri;
			}
		}
		return null;
	}

	/**
	 * collecting list of transformers after the battle
	 * 
	 * @param ArrayList
	 *            of Transformer, transformersList before the battle
	 * @return ArrayList of Transformer, transformersList after the battle
	 */
	public ArrayList<Transformer> collectList(
			ArrayList<Transformer> transformersList) {
		int numberOfBattles = 0;
		for (int i = 0; i < transformersList.size(); i++) {
			Transformer transformeri = transformersList.get(i);
			for (int j = i + 1; j < transformersList.size(); j++) {
				Transformer transformerj = transformersList.get(j);
				Transformer transformerCourage = compareBasedOnCourage(
						transformeri, transformerj);
				Transformer transformerSkill = compareBasedOnSkill(
						transformeri, transformerj);
				if (transformerCourage != null) {
					transformersList.remove(transformerCourage);
					numberOfBattles++;
				} else if (transformerSkill != null) {
					transformersList.remove(transformerSkill);
					numberOfBattles++;
				}
				// handling tie:both Transformers are considered destroyed
				else if (transformeri.getOverallRating() == transformerj
						.getOverallRating()) {
					transformersList.remove(transformeri);
					transformersList.remove(transformerj);
				}

			}

		}
		// printing number of battles
		System.out.println(numberOfBattles + " battle");
		return transformersList;
	}

	/**
	 * Determining the winner with highest overall rating
	 * 
	 * @param transformersList
	 *            , ArrayList of Transformer after the battle
	 * @return the winner
	 */
	public Transformer getWinner(ArrayList<Transformer> transformersList) {
		Transformer winner = transformersList.get(0);
		for (int k = 1; k < transformersList.size(); k++) {
			Transformer transformerk = transformersList.get(k);
			if (winner.getOverallRating() < transformerk.getOverallRating()) {
				winner = transformerk;
			}

		}
		return winner;
	}

	/**
	 * @param transformer
	 * @return the type of the Transformer
	 */
	public String getTeamType(Transformer transformer) {
		String team = "";
		if (transformer.getType() == 'D') {
			team = "(Decepticons):";
		} else {
			team = "(Autobots):";
		}
		return team;
	}

	// Producing result of the battles
	public void getResult(ArrayList<Transformer> transformersList) {
		if (specialRuleApplies(transformersList)) {
			System.out.println(printSpecialWinner(transformersList));
		} else {
			transformersList = collectList(transformersList);
			Transformer winner = getWinner(transformersList);
			String winnerName = winner.getName();
			System.out.println("Winning team " + getTeamType(winner)
					+ winnerName);
			transformersList.remove(winner);
			System.out.println("Survivors from the losing team "
					+ getTeamType(transformersList.get(0))
					+ transformersList.get(0).getName());

		}
	}

	public static void main(String[] args) {
		ArrayList<Transformer> transformerList = new ArrayList<Transformer>();
		transformerList.add(new Transformer("Hubcap", 'A', 4, 4, 4, 4, 4, 4, 4,
				4));
		transformerList.add(new Transformer("Soundwave", 'D', 8, 9, 2, 6, 7, 5,
				6, 10));
		transformerList.add(new Transformer("Bluestreak", 'A', 6, 6, 7, 9, 5,
				2, 9, 7));
		Battle battle = new Battle();
		ArrayList<Transformer> transformers = battle
				.getSortedList(transformerList);
		battle.getResult(transformers);

	}

}
